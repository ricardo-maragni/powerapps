# Carregar últimos itens de uma base de dados
Obs: Fórmula feita com os 1000 últimos itens

## 1º Jeito
```powerfx
ClearCollect(colMyItems,FirstN(Sort(Terminer_V3,ID,SortOrder.Descending),1000))
```

## 2º Jeito
```powerfx
ClearCollect(colMyItems_Desc,FirstN(Sort(Terminer_V3,ID,SortOrder.Descending),10));
ClearCollect(colMyItems,colMyItems_Desc);
Clear(colMyItems_Desc);
```
