# Galerias

## Galeria com ordem de IDs, filtros de texto e comboboxes

Formatação em pt-br
```powerfx
//Inicia ordenamento pela coluna ID
SortByColumns(

//Inicia pesquisa e filtro, utilizando SuaBaseDeDados e SuaSearchBox
Search(Filter(SuaBaseDeDados;

//Inicia filtros pelas ComboBoxes

IsBlank(SuaCombobox1.SelectedItems.Value)||IsEmpty(SuaCombobox1.SelectedItems)|| SuaColuna1 in SuaCombobox1.SelectedItems;
IsBlank(SuaCombobox2.SelectedItems.Value)||IsEmpty(SuaCombobox2.SelectedItems)|| SuaColuna2 in SuaCombobox2.SelectedItems;
IsBlank(SuaCombobox3.SelectedItems.Value)||IsEmpty(SuaCombobox3.SelectedItems)|| SuaColuna3 in SuaCombobox3.SelectedItems);

//Finaliza filtros pelas ComboBoxes

//Finaliza pesquisa e filtro, utilizando SuaBaseDeDados e SuaSearchBox
SuaSearchBox.Text; "Title");

//Finaliza ordenamento pela coluna ID, de forma decrescente
"ID";SortOrder.Descending)
```
