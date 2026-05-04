# Como criar ícones / vetores

1. Acessar o https://lucide.dev/

2. Pesquisar o ícone que você quer

3. Clicar em copy svg

4. Substituir no código:

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
