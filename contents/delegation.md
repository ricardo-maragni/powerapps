# Quebrando a delegação

## 1 - Método simples

```powerfx
ClearCollect(colMyItems,FirstN(Sort(SolicitacaoDeNovoEmbarqueDeImportacao,ID,SortOrder.Descending),2000));
```


## 2 - Dividindo a Sharepoint List em 2 partes e depois agrupar

```powerfx
// 1) Pega os primeiros 3000 (IDs menores)
ClearCollect(
    colMyItems_Asc,
    FirstN(
        Sort(
            Filter(
                'Acompanhamento de Solicitações',
                'Created By'.Email = varMyMail
            ),
            ID,
            SortOrder.Ascending
        ),
        3000
    )
);
 
// 2) Pega os últimos 3000 (IDs maiores)
ClearCollect(
    colMyItems_Desc,
    FirstN(
        Sort(
            Filter(
                'Acompanhamento de Solicitações',
                'Created By'.Email = varMyMail
            ),
            ID,
            SortOrder.Descending
        ),
        3000
    )
);
 
// 3) Une sem duplicar (colMyItems = "todos")
ClearCollect(colMyItems, colMyItems_Asc);
Collect(colMyItems, Filter(colMyItems_Desc, Not(ID in colMyItems_Asc.ID)));
 
Clear(colMyItems_Asc);
Clear(colMyItems_Desc);
```
