# Barra de progresso
Você pode utilizar para medir o progresso de determinados contextos dentro do aplicativo.

<progress></progress>

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
