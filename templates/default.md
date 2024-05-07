# INVOICE


## Invoice Details

- Invoice No: 1
- Issue Date: {{ (time.Now).UTC.Format "Jan 2, 2006" }}

## Personal information

- Name: {{ (ds "data").personal_info.name }}
- ID: {{ (ds "data").personal_info.id_number }}
- Address: {{ (ds "data").personal_info.address }}
- Phone: {{ (ds "data").personal_info.phone }}
- Email: {{ (ds "data").personal_info.email }}


## Company Details

- Company Name: {{ (ds "data").company_info.name }}
- Company Address: {{ (ds "data").company_info.address }}
- RUT: {{ (ds "data").company_info.id }}
- Company Email: {{ (ds "data").company_info.email }}

## Invoice Summary

{{ $total := 0 }}
| Item | Description                          | Quantity | Rate    | Amount   |
|------|--------------------------------------|----------|---------|----------|
{{ range $index, $element := (ds "data").invoice_items -}}
{{- $entry_total := mul $element.rate $element.quantity }}
{{- $total = add $total $entry_total -}}
| {{ add $index 1 }} | {{ $element.description }} | {{ $element.quantity }} | {{ $element.rate }} | {{ $entry_total }} USD |
{{ end -}}
|              | Total                      |                         |                     | {{ $total }} USD       |

## Payment Details

- Account holder: {{ (ds "data").payment_info.account_holder }}
- Bank: {{ (ds "data").payment_info.bank_name }}
- Account: {{ (ds "data").payment_info.account_number }}
- Account type: {{ (ds "data").payment_info.account_type }}
- Swift ID: {{ (ds "data").payment_info.swift_id }}

