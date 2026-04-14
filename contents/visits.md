# Registrar visitas e inputs em base de dados

## Visitas

Adicionar no OnStart do app:
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

Adicionar no OnSelect do botão de input:
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
