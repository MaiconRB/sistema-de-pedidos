# sistema-de-pedidos

Sistema de pedidos full-stack: API REST em **ASP.NET Core** (arquitetura MVC) e frontend **Angular**, com CRUD completo de fornecedores, produtos e pedidos.

![.NET 7](https://img.shields.io/badge/.NET-7-512BD4?logo=dotnet&logoColor=white)
![C#](https://img.shields.io/badge/C%23-239120?logo=csharp&logoColor=white)
![Angular](https://img.shields.io/badge/Angular-16-DD0031?logo=angular&logoColor=white)
![EF Core](https://img.shields.io/badge/EF%20Core-SQLite-003B57?logo=sqlite&logoColor=white)

## Funcionalidades

CRUD de três entidades relacionadas, expostas via `api/[controller]`:

| Controller | Rotas |
|---|---|
| `FornecedorController` | `GET/POST /api/fornecedor`, `PUT/DELETE /api/fornecedor/{id}` |
| `ProdutoController` | `GET/POST /api/produto`, `PUT/DELETE /api/produto/{id}` |
| `PedidoController` | `GET/POST /api/pedido`, `GET /api/pedido/ByFornecedor/{fornecedorId}`, `PUT/DELETE /api/pedido/{id}` |

No frontend, a SPA em Angular consome essas rotas com módulos dedicados para `dashboard`, `fornecedor`, `produto` e `pedido`.

## Estrutura

```
sistema-de-pedidos/
├── Backend/            # API ASP.NET Core (MVC) + EF Core + SQLite
│   ├── Controllers/
│   ├── Data/           # DataContext e Repository genérico
│   ├── Models/
│   └── Migrations/
└── Frontend/           # SPA Angular + Bootstrap
    └── src/app/
        ├── dashboard/
        ├── fornecedor/
        ├── produto/
        └── pedido/
```

## Rodando localmente

Pré-requisitos: [.NET 7 SDK](https://dotnet.microsoft.com/download) e [Node.js](https://nodejs.org/) com Angular CLI.

**Backend**

```bash
cd Backend
dotnet restore
dotnet ef database update
dotnet run
```

A API sobe em `http://localhost:5017` (o Swagger fica em `/swagger`).

**Frontend**

```bash
cd Frontend
npm install
ng serve
```

A aplicação fica disponível em `http://localhost:4200`, consumindo a API configurada em `src/environments/environment.ts`.
