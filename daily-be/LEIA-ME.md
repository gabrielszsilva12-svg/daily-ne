# Daily Front Comercial — como colocar no ar

São dois passos: criar o banco de dados no Firebase (uma vez só) e subir os arquivos na Vercel.

## 1. Firebase (banco de dados em tempo real)

1. Entre em https://console.firebase.google.com e clique em **Adicionar projeto**. Nome sugerido: `daily-be`. Pode desativar o Google Analytics.
2. No menu da esquerda, **Build → Firestore Database → Criar banco de dados**. Escolha a região `southamerica-east1 (São Paulo)` e o modo **produção**.
3. Ainda no Firestore, abra a aba **Regras**, apague o que estiver lá, cole o conteúdo do arquivo `firestore.rules` e clique em **Publicar**.
4. No menu, **Build → Authentication → Vamos começar → Método de login → Anônimo → Ativar → Salvar**.
5. Clique na engrenagem ⚙️ (Configurações do projeto) → role até **Seus apps** → ícone **</>** (Web). Dê um apelido (`daily`) e clique em **Registrar app**. Vai aparecer um bloco `firebaseConfig = { apiKey: ..., authDomain: ..., ... }`.
6. Abra o arquivo `firebase-config.js` e troque os valores pelos do seu `firebaseConfig`. Se quiser, preencha também `senhaTime` e `senhaGestao`.

## 2. Vercel (o link)

1. Entre em https://vercel.com (pode ser a mesma conta da Loja Conceito) → **Add New → Project**.
2. O jeito mais simples: arraste a pasta inteira (com `index.html`, `firebase-config.js`, `seed.json`, `firestore.rules` e a pasta `mascote`) na área de upload, ou suba num repositório do GitHub e importe.
3. Framework: **Other**. Não precisa de build. Clique em **Deploy**.
4. Em **Settings → Domains** dá para trocar o nome para algo como `daily-be.vercel.app`.

## 3. Depois de subir

- No **Firebase → Authentication → Configurações → Domínios autorizados**, adicione o domínio da Vercel (ex.: `daily-be.vercel.app`).
- Abra o link. Na primeira vez, o site copia sozinho os cards e o lembrete que estavam na versão do Claude (arquivo `seed.json`). Isso acontece uma vez só.
- Pronto: todo mundo que abrir o link vê e mexe nas mesmas informações, em tempo real.

## Bom saber

- As senhas ficam no próprio site; afastam curiosos, mas quem entende de código consegue achar. Para algo mais fechado, dá para trocar depois por login com a conta Microsoft da empresa.
- O plano gratuito do Firebase aguenta com folga o uso de um time desse tamanho.
- Para mudar a senha ou o Firebase no futuro, edite `firebase-config.js` e suba de novo na Vercel.
