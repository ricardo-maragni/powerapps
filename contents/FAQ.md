# FAQ
Modelo de FAQ para utilizar em seus aplicativos, disponibilizando os contatos da sua área.

```powerfx
With({
EstiloHeading: "border: 1px solid lightgray; background:#001e50; color:white",
EstiloBorda:"border: 1px solid lightgray"
},
"
<!DOCTYPE html>
<html lang='pt-BR'>
<head>
    <meta charset='UTF-8'>
    <meta name='viewport' content='width=device-width, initial-scale=1.0'>
    <title>FAQ</title>
    <style>body{font-family: arial}</style>
</head>
<body>
<H1 style='text-align: center;'>FAQ</H1>
<hr width=100% size=2><br>
<h2>1) Com quem posso entrar em contato para sugerir melhorias ou tirar dúvidas?</h2>
<table width='100%' cellpadding='10px' style='border-collapse: collapse;'>
<colgroup><col width='50%'><col width='50%'></colgroup>
<tr>
<th style='"&EstiloHeading&"'>E-mail</th>
<th style='"&EstiloHeading&"'>Atuação</th>
</tr>
"
&
Concat(
Table(
{Title: "nome@e-mail_1",Permissao: "Key-User"},
{Title: "nome@e-mail_2",Permissao: "Desenvolvedor"},
{Title: "nome@e-mail_3",Permissao: "Designer"},
{Title: "nome@e-mail_4",Permissao: "Digilog"},
{Title: "nome@e-mail_5",Permissao: "Digilog"}
),
"
<tr>
<td style='"&EstiloBorda&"'>"& Title & "</td>
<td style='"&EstiloBorda&"'>"& Permissao &"</td>
</tr>
"
)
&
"
</table>
</body>
</html>
"
)
```
