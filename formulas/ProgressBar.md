# Barra de progresso
Você pode utilizar para medir o progresso de determinados contextos dentro do aplicativo.

## Exemplos (mais simples de copiar e colar)

## Exemplo 1: Barra de progresso simples
```powerfx
"<progress value='75' max='100'></progress>"
```

## Exemplo 2: Barra de progresso simples + largura e autura definidas
```powerfx
"<progress value='75' max='100' style='width:100%;height:10px'></progress>"
```

## Exemplo 3: Barra de progresso simples + largura e altura definidas + legenda centralizada
```powerfx
"<div style='position: relative; width: 100%; height: 80px;'> 
<progress value='60' max='100' style='width: 100%; height: 100%; accent-color:blue'></progress> 
<span style=' position: absolute; top: 0; left: 0; width: 100%; height: 100%; display: flex; align-items: center; justify-content: center; font-size: 20px; font-weight: bold; color: white; '> 60% </span> </div>"
```

## Exemplo 4: Barra de progresso simples + largura e altura definidas + legenda à esquerda com margem esquerda de 20px
```powerfx
"<div style='position: relative; width: 100%; height: 80px;'> 
<progress value='8' max='100' style='width: 100%; height: 100%; accent-color:blue'></progress> 
<span style=' position: absolute; top: 0; left: 0; width: 100%; height: 100%; display: flex; align-items: center; justify-content: left; margin-left: 20px; font-size: 20px; font-weight: bold; color: white; '> 8% </span> </div>"
```

<hr>

## Casos aplicados (mais complexo de copiar e colar)

## Caso aplicado 1 (Exemplo 3 aprimorado)
O objetivo desse caso aplicado era criar uma base de progresso com os campos já preenchidos de um formulário.
Foi necessário criar algumas <b>constantes locais</b> para fazer essa contagem de campos já preenchidos.
Para facilitar o entendimento, dividi a fórmula com comentários e no comentário final fica disponibilizado o HTML baseado no Exemplo 3 (Barra de progresso simples + largura e altura definidas + legenda centralizada)

```powerfx
//CONSTANTES PT.1 -> Criação de uma base de dados que verifica o que está preenchido
With({
Base_loc:
Split(
//Seção 1 do formulário
IsBlank(DataCardValue3.Text) & "|" & IsBlank(DataCardValue4.Selected.Value) & "|" & IsBlank(DataCardValue5.Selected.Value) & "|" &
IsBlank(DataCardValue6.Text) & "|" & IsBlank(DataCardValue7.SelectedDate) & "|" & IsBlank(DataCardValue8.Text) & "|" &
IsBlank(DataCardValue9.Selected.Value) & "|" & IsBlank(DataCardValue10.Text) & "|" & IsBlank(DataCardValue11.Text) & "|" &
IsBlank(DataCardValue12.Selected.Value) & "|" & IsBlank(DataCardValue13.Text) & "|" & IsBlank(DataCardValue14.Selected.Value) & "|" &
IsBlank(DataCardValue15.Text) & "|" & IsBlank(DataCardValue16.Text) & "|" & IsBlank(DataCardValue17.Text) & "|" &
IsBlank(DataCardValue18.Selected.Value) & "|" &
//Seção 2 do formulário
IsBlank(DataCardValue19.Text) & "|" & IsBlank(DataCardValue20.Selected.Value) & "|" & IsBlank(DataCardValue21.Selected.Value) & "|" &
IsBlank(DataCardValue22.Text) & "|" & IsBlank(DataCardValue23.Selected.Value) & "|" & IsBlank(DataCardValue24.Text) & "|" & 
IsBlank(DataCardValue25.Text) & "|" & IsBlank(DataCardValue26.Text) & "|" & IsBlank(DataCardValue27.Text),"|")},
//CONSTANTES PT.2 -> Contagem de quantos campos existem no total e contagem de quantos campos já foram preenchidos
With({
ContagemCamposTotal_loc:CountRows(Base_loc),
ContagemCamposPreenchidos_loc:CountRows(Filter(Base_loc,Value="false"))},
//CONSTANTES PT.3 -> Criação da constante progresso
With({
Progresso_loc: (ContagemCamposPreenchidos_loc/ContagemCamposTotal_loc)*100},
//HTML -> Criação da barra de progresso utilizando HTML e CSS Inline
" 
<div style='position: relative; width: 100%; height: 80px;'> 
<progress value='"&Progresso_loc&"' max='100' style='width: 100%; height: 100%; accent-color:blue'></progress> 
<span style=' position: absolute; top: 0; left: 0; width: 100%; height: 100%; display: flex; align-items: center; justify-content: center; font-size: 20px; font-weight: bold; color: white; '> "&Progresso_loc&"% </span> </div>
")))
```

