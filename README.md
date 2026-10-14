# yol

a self-hosted, port-free tunneling application for development stacks. _yol_ is
Turkish for "road".

yol lets developers expose services running on their systems, even when they are
behind a firewall or NAT.

## Why yol?

- it's a free and open-source alternative to paid tunneling platforms such as
  `ngrok`
- it uses your traffic on your own server and domain, so no third party in the
  middle
- it uses hostnames instead of port numbers, so you don't have to deal with them
- it lets multiple services share the same port (e.g. multiple postgres
  instances run on 5432)
- it's designed to be a sidekick that you can use from day one
- it works with your Docker Compose setup, reads hostnames from `compose.yml`
  where available
- it has built-in inspector for observing, replaying and exporting requests
- it's a single portable Go binary that's easy to bundle or copy

## Motivation

Most existing solutions in this space are commercial services. ngrok provides
limited free usage, while many alternatives require paid plans and are often
closed-source. They also require your development traffic to pass through
infrastructure operated by a third party.

Our goal with **Yol** is simple: build a free and open-source developer tool
that we—and other developers—can comfortably self-host, trust, use, inspect,
modify and contribute to.

**Your server. Your domain. Your traffic. Your Yol.**

## 🚀 Jumpstart

Ensure that [Homebrew](https://brew.sh/) 7.0.0 or higher is installed on your
system first.

### Install the CLI

```bash
# Homebrew
brew install bilus/tap/yol
```

### Workflow

`yol init` reads the `compose.yml` (Docker Compose file) and updates their own
records.

```bash
$ yol init

✓ Yol initialized with 3 service(s)

$ docker compose up -d

$ yol status

  dashboard   http://dashboard.localhost      compose service dashboard (3000)
  api         http://api.localhost            compose service api (8080)
  db          tcp://db.localhost:5432         compose service db (5432)
  inspector   http://localhost:4040

$ psql -h db.localhost -U postgres
```

### Going public

```bash
$ yol expose dev.example.org

✓ Exposed 2 services(s) to dev.example.org
  → dashboard     https://dashboard.dev.example.org
  → api           https://api.dev.example.org
  ✓ db            local only
```

## Contributors

<!-- CONTRIBUTORS:START -->
<table>
  <tr>
    <td align="center"><a href="https://github.com/vigo"><img src="https://avatars.githubusercontent.com/u/82952?v=4?s=80" width="80" /><br /><sub>vigo</sub></a></td>
    <td align="center"><a href="https://github.com/eser"><img src="https://avatars.githubusercontent.com/u/866558?v=4?s=80" width="80" /><br /><sub>eser</sub></a></td>
  </tr>
</table>
<!-- CONTRIBUTORS:END -->

## 🙋🏻 FAQ

### Want to report a bug or request a feature?

If you're going to report a bug or request a new feature, please ensure first
that you comply with the conditions found under our code of conduct. After that,
you can report an issue or request using
[GitHub Issues](https://github.com/bilusteknoloji/yol/issues). Thanks in
advance.

### Want to contribute?

It is publicly open for any contribution from the community. Bug fixes, new
features and additional components are welcome.

If you're interested in becoming a contributor and enhancing the ecosystem,
please start by reading through our [CONTRIBUTING.md](CONTRIBUTING.md).

If you're not sure where to begin, take a look at the
[issues](https://github.com/bilusteknoloji/yol/issues) labeled
`good first issue` and `help wanted`. Reviewing closed issues can also give you
a sense of the types of contributions we're looking for and you can tackle.

If you're already an experienced OSS contributor, let's take you to the shortest
path: To contribute to the codebase, just fork the repo, push your changes to
your fork, and then submit a pull request.

### Requirements

- Go 1.27.2 or higher (https://go.dev/)

### Versioning

This project follows [Semantic Versioning](https://semver.org/). For the
versions available, see the
[tags on this repository](https://github.com/bilusteknoloji/yol/tags).

### License

This project is licensed under the Apache 2.0 License. For further details,
please see the [LICENSE](LICENSE) file.
