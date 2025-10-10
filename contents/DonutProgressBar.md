# Barra de progresso circular tipo rosca
Você pode utilizar para medir o progresso de determinados contextos dentro do aplicativo.

```powerfx
"
<!-- Barra de progresso circular tipo rosca -->
<div style='height:500px; aspect-ratio:1/1; border-radius:50%; 
            background:conic-gradient(#001e50 0% "&Gallery1.Selected.Value&"%, #eee "&Gallery1.Selected.Value&"% 100%);
            display:flex; align-items:center; justify-content:center; 
            position:relative; font-family:sans-serif; font-size:5vh; 
            color:#001e50;'>

  <!-- Furo central -->
  <div style='position:absolute; width:60%; height:60%; background:#fff; 
              border-radius:50%; display:flex; align-items:center; 
              justify-content:center;'>
    "&Gallery1.Selected.Value&"%
  </div>
</div>
"
```
