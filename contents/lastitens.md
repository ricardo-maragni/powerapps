# Carregar últimos itens de uma base de dados
Obs: A quantidade máxima de últimos itens é igual ao número máximo de delegação que pode haver num app. No caso 2000.

```powerfx
ClearCollect(colMyItems,FirstN(Sort(Terminer_V3,ID,SortOrder.Descending),2000))
```
