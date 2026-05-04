# Como criar ícones / vetores

1. Copie o código do .svg em algum desses sites:

Ícones -> https://lucide.dev/

Fundos -> https://app.haikei.app/

2. Substituir no código:

```
"data:image/svg+xml;utf8," & EncodeUrl(...)
```

Ou por esse caso queira substituir cor

```
//Padrão
"data:image/svg+xml;utf8," 
& Substitute( 
//Cole o link svg aqui
"", 
//Escolha a cor aqui
"currentColor", "%23ffffff" )
```
