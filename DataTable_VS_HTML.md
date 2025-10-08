# DataTable VS HTML

O cenário apresentado para avaliar as diferenças entre o DataTable e HTML consiste num Power Apps conectado à uma base no Sharepoint.
A base de dados contém as colunas PartNumbers e Quantidade de PartNumbers que dividem as informações entre pipes " | ".
Esse aplicativo contém a Gallery1 conectada à base do Sharepoint e agora precisamos criar uma tabela para visualizar os Part Numbers e suas respectivas quantidades.

## Via DataTable o código ficou assim:
``` power fx
With({
PartNumber_loc:Split(Gallery1.Selected.PartNumbers," | "),
QuantidadePartNumbers_loc:Split(Gallery1.Selected.QuantidadePartNumbers," | ")},
ForAll(
Sequence(CountRows(PartNumber_loc)),
{
PartNumbers: Last(FirstN(PartNumber_loc, Value)).Value,
QuantidadePartNumbers:Last(FirstN(QuantidadePartNumbers_loc, Value)).Value
}))
```

## Via HTML o código ficou assim:
``` html/css/powerfx
//CONSTANTES PT.1
With({
//ESTILIZAÇÃO CSS
EstiloHeading: "border: 1px solid lightgray; background:#004aad; color:white",
EstiloBorda:"border: 1px solid lightgray",
//COLUNAS
PartNumber_loc:Split(Gallery1.Selected.PartNumbers," | "),
QuantidadePartNumbers_loc:Split(Gallery1.Selected.QuantidadePartNumbers," | ")},
//CONSTANTES PT.2
With({
//BASE DE DADOS
Base_loc:
ForAll(
Sequence(CountRows(PartNumber_loc)),
{
PartNumbers: Last(FirstN(PartNumber_loc, Value)).Value,
QuantidadePartNumbers:Last(FirstN(QuantidadePartNumbers_loc, Value)).Value
})},
//HTML
"
<!DOCTYPE html>
<html lang='en'>
<head>
    <meta charset='UTF-8'>
    <meta name='viewport' content='width=device-width, initial-scale=1.0'>
    <title>PartNumbers</title>
    <style>body{font-family: arial}</style>
</head>
<body>

<table width='100%' cellpadding='10px' style='border-collapse: collapse;'>
<tr>
<th style='"&EstiloHeading&"'>PartNumbers</th>
<th style='"&EstiloHeading&"'>Quantidade de PartNumbers</th>
</tr>
"
&
Concat(Base_loc
,
"
<tr>
    <td style='"&EstiloBorda&"'>"&PartNumbers&"</td>
    <td style='"&EstiloBorda&"'>"&QuantidadePartNumbers&"</td>
</tr>
"
)
&
"
</table>
</body>
</html>
"
))
```
