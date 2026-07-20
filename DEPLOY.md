# DEPLOY DO SITE NEOPACK

## Opção 1: GitHub Pages (grátis)

1. Crie uma conta em https://github.com
2. Crie um repositório chamado `seunome/neopack`
3. Faça upload de todos os arquivos da pasta `NeoPack-Site/`
4. Vá em Settings > Pages > Source: "Deploy from branch"
5. Selecione `main` / `root`
6. Pronto! Seu site em: `https://seunome.github.io/neopack`

## Opção 2: Netlify (grátis, mais fácil)

1. Crie conta em https://netlify.com
2. Arraste a pasta `NeoPack-Site/` para o Netlify Drop
3. Pronto! Site online em minutos

## Opção 3: Vercel (grátis)

1. Crie conta em https://vercel.com
2. Conecte seu GitHub ou arraste a pasta
3. Pronto!

## CONFIGURAR PAGAMENTOS

### Stripe
1. Crie conta em https://stripe.com
2. Crie um Payment Link: Products > Create Payment Link
3. Cole o link no botão "Comprar" do `index.html`

### Hotmart
1. Crie conta em https://hotmart.com
2. Crie um produto digital
3. Copie o checkout URL e cole no botão do `index.html`

### PayPal
1. Crie conta em https://paypal.com
2. Crie um botão "Buy Now" em PayPal Buttons
3. Cole o código no `index.html`

## REDIRECIONAR APÓS COMPRA

No Stripe/Hotmart/PayPal, configure o redirect para:
`https://seunome.github.io/neopack/download.html`

O cliente pagou → redireciona pro `download.html` → baixa o ZIP.

## ESTRUTURA DO SITE

```
NeoPack-Site/
├── index.html              # Landpage de vendas
├── download.html           # Página pós-compra
├── DEPLOY.md               # Este guia
├── .gitignore
└── zip/
    └── NeoPack-v1.0.0.zip  # Produto para download
```
