# 🍇 Uvas do Ló — Site Institucional & Sistema de Agendamento

Site oficial da **Uvas do Ló**, propriedade rural localizada em **Aracê, Domingos Martins — ES**, especializada em cultivo de uvas e experiências de piquenique no parreiral.

---

## 🌐 Acesso ao Site

| Ambiente | URL |
|---|---|
| **Site principal** | `https://profound-churros-6bf2f9.netlify.app` |
| **Painel Admin** | `https://profound-churros-6bf2f9.netlify.app/admin` |

---

## 📁 Estrutura de Arquivos

```
uvasdolo/
  ├── index.html      → Site principal (renomeado de uvas-do-lo.html)
  ├── admin.html      → Painel administrativo
  └── _redirects      → Configuração de rotas do Netlify
```

---

## 🖥️ Sobre o Site

Site institucional **one-page** com as seguintes seções:

- **Hero** — Capa com imagem do parreiral e chamada para agendamento
- **Nossa História** — Trajetória da família Ló desde 2013
- **Nossas Uvas** — 7 variedades cultivadas com descrição e época de colheita
- **Piquenique** — Experiência, kits, preços e formulário de agendamento
- **Galeria** — Fotos reais do piquenique com carrossel e lightbox
- **Contato** — Informações de localização e funcionamento

### 🧺 Formulário de Agendamento (5 etapas)

1. **Kit** — Escolha entre Kit 2, 4 ou 6 pessoas
2. **Dia** — Datas disponíveis cadastradas pelo admin
3. **Horário** — Sessões de 1h30 (horários ocupados aparecem bloqueados)
4. **Dados** — Nome, WhatsApp, e-mail, crianças acima de 7 anos e observações
5. **Resumo** — Confirmação e envio via WhatsApp

> 👶 Crianças até 7 anos não pagam e não contam nas vagas do kit.

---

## 🔒 Painel Administrativo

### Acesso

| Campo | Valor |
|---|---|
| **URL** | `/admin` |
| **E-mail** | `uvasdolo@gmail.com` |
| **Senha** | *(definida no Firebase Authentication)* |

> ⚠️ Em caso de esquecimento de senha, use a opção **"Esqueci minha senha"** na tela de login — um link será enviado ao e-mail cadastrado.

---

### 🎛️ Funcionalidades do Admin

#### Conteúdo do Site
| Seção | O que pode editar |
|---|---|
| **Capa (Hero)** | Título, subtítulo, pílula, botões e imagem de fundo |
| **Nossa História** | Título e 4 parágrafos de texto + foto |
| **Nossas Uvas** | Nome, época, descrição e foto de cada uma das 7 uvas |
| **Piquenique** | Textos, preços dos kits, temporada, sinal e WhatsApp |
| **Galeria** | 5 fotos com legenda (via link do Imgur) |
| **Contato** | Localização, WhatsApp, e-mail e horário de funcionamento |

#### Agendamentos
| Aba | Função |
|---|---|
| **Dias Disponíveis** | Adicionar ou remover datas da temporada |
| **Horários** | Adicionar ou remover horários de atendimento |
| **Reservas** | Ver, confirmar ou cancelar solicitações dos clientes |

---

## 📸 Como Trocar Fotos (Imgur)

1. Acesse [imgur.com](https://imgur.com)
2. Clique em **"New post"** e arraste a foto
3. Após o upload, clique com o **botão direito** na imagem → **"Copiar endereço da imagem"**
4. O link terá o formato: `https://i.imgur.com/xxxxxxx.jpg`
5. Cole o link no campo correspondente no painel admin
6. Clique em **💾 Salvar**

---

## 🔥 Firebase

O projeto utiliza o **Firebase** (plano Spark — gratuito) para:

| Serviço | Uso |
|---|---|
| **Authentication** | Login do painel admin |
| **Firestore** | Banco de dados (datas, horários, reservas, conteúdo) |

### Coleções do Firestore

| Coleção | Descrição |
|---|---|
| `site` | Textos e imagens editáveis pelo admin |
| `dias` | Datas disponíveis para agendamento |
| `horarios` | Horários de atendimento |
| `reservas` | Solicitações de agendamento dos clientes |

### Índice necessário

| Coleção | Campos | Tipo |
|---|---|---|
| `reservas` | `dataVisita` + `status` | Manual / Crescente |

### Regras de Segurança

```
rules_version = '2';
service cloud.firestore {
  match /databases/{database}/documents {
    match /site/{doc} {
      allow read: if true;
      allow write: if request.auth != null;
    }
    match /dias/{doc} {
      allow read: if true;
      allow write: if request.auth != null;
    }
    match /horarios/{doc} {
      allow read: if true;
      allow write: if request.auth != null;
    }
    match /reservas/{doc} {
      allow read, create: if true;
      allow update, delete: if request.auth != null;
    }
  }
}
```

---

## 🚀 Hospedagem (Netlify)

O site está hospedado no **Netlify** (plano gratuito).

### Como fazer novo deploy

1. Acesse [app.netlify.com](https://app.netlify.com)
2. Clique no site **profound-churros-6bf2f9**
3. Vá em **"Deploys"**
4. Arraste a pasta com os 3 arquivos (`index.html`, `admin.html`, `_redirects`)

### Arquivo `_redirects`

Necessário para a rota `/admin` funcionar:
```
/admin        /admin.html    200
/admin/       /admin.html    200
```

---

## 📱 WhatsApp

O número configurado para receber agendamentos e mensagens é:

**Cássio Fellipe — (21) 96529-4486**

Para alterar o número, edite no painel admin em **Piquenique → WhatsApp**.

---

## 🛠️ Tecnologias Utilizadas

| Tecnologia | Uso |
|---|---|
| HTML5 + CSS3 + JavaScript | Site e painel admin (sem frameworks) |
| Firebase Firestore | Banco de dados em tempo real |
| Firebase Authentication | Login seguro do admin |
| Netlify | Hospedagem gratuita |
| Imgur | Armazenamento de imagens |
| Google Fonts | Cormorant Garamond + Jost |

---

## 📞 Contato

**Uvas do Ló**
📍 Aracê, Domingos Martins — ES
📱 (21) 96529-4486 · Cássio Fellipe
🌐 [profound-churros-6bf2f9.netlify.app](https://profound-churros-6bf2f9.netlify.app)

---

*Desenvolvido com ❤️ para a família Ló — Temporada 2026*
