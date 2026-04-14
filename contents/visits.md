# Registrar visitas e inputs em base de dados

## Visitas

```powerfx
If(
    IsBlank(varRegistroAcessoID),
    Set(
        varRegistroAcessoID,
        Patch(
            RegistrosApp,
            Defaults(RegistrosApp),
            {
                NomeApp: "Lote Mínimo", //"Nome do app"
                User: User().FullName,
                DataAcesso: Now(),
                TipoAcesso: { Value: "Acesso" }
            }
        ).ID
    )
)
```

## Inputs

```powerfx
If(
    !IsBlank(varRegistroAcessoID),
    Patch(
        RegistrosApp,
        LookUp(RegistrosApp, ID = varRegistroAcessoID),
        {
            TipoAcesso: { Value: "Registro" }
        }
    )
)
```
