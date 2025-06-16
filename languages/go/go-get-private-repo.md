# Quando o `go get` não colabora com repositórios privados: como forçar o uso de SSH (e evitar dor de cabeça)

Você já tentou rodar um `go get` em um repositório privado e se deparou com aquele erro misterioso de permissão negada? Pois é, eu também. E olha… quebrar a cabeça por causa disso é mais comum do que deveria. 😅

Recentemente, precisei instalar uma lib interna via Go Modules, e, claro, o repositório era privado. A solução parecia óbvia: `go get github.com/caiomarcatti12/meu-repo-secreto-e-privado`. Só que não funcionou. E aí começa a saga…

---

## O que tá pegando?

O `go get` por padrão tenta acessar o repositório via **HTTPS**, o que não funciona bem com repositórios privados — a menos que você configure um token ou autenticação via HTTPS (nada prático, vamos combinar?).

Se você, assim como eu, prefere usar **SSH** pra gerenciar acesso ao GitHub (com chave pública e privada), então bora forçar o Go a seguir esse caminho.

---

## 🚀 Como forçar o `go get` a usar SSH?

###  1. Configure o `.gitconfig` para reescrever HTTPS → SSH

Você pode automatizar essa substituição com:

```bash
git config --global url."git@github.com:".insteadOf "https://github.com/"
```

Com isso, sempre que o Go tentar baixar algo de `https://github.com/...`, o Git intercepta e redireciona pra `git@github.com:...`. Mágico, né?

---

### 2. Repositório privado? Use `GOPRIVATE`

Se o repositório for privado, o Go pode travar porque tenta resolver via proxy público. Aí entra o `GOPRIVATE`:

```bash
export GOPRIVATE=github.com/caiomarcatti12/*
```

Coloca isso no seu `.bashrc`, `.zshrc` ou onde preferir. Assim o Go entende que esses domínios devem ser tratados de forma especial, sem proxy e sem verificação de sumário público.

---

## 💡 Exemplo prático completo

```bash
export GOPRIVATE=github.com/caiomarcatti12/*
git config --global url."git@github.com:".insteadOf "https://github.com/"
go get github.com/caiomarcatti12/meu-repo-secreto-e-privado
```

Depois disso? Tudo flui! E o Go passa a respeitar seu esquema de autenticação via SSH.

---

## 👀 O começo das suas reflexões

- SSH é mais seguro e prático pra repositórios privados? Sim!
- Vale a pena configurar? Com certeza!
- Mas… **você sabe mesmo o que tá trazendo pro seu código quando dá um `go get`?**

E aí, como você lida com isso no seu time? Já passou por algum perrengue por confiar demais no `go get` padrão? Bora trocar experiências nos comentários! 🛠️✨

#ArrumeiParaCabeça #GoLang #SSHNaVeia #DependenciaPrivada
