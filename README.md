# sonar-buggy-example

Projeto Maven (Java 17) para analisar o `BuggyExample.java` no SonarCloud.

O código-fonte em `src/main/java/BuggyExample.java` é o código original, **sem nenhuma alteração**. Os demais arquivos são apenas a infraestrutura de build e CI necessária para a análise.

## Configuração no SonarCloud

1. Suba o projeto para um repositório no GitHub.
2. Em <https://sonarcloud.io>, importe o repositório e anote a **Organization Key** e o **Project Key**.
3. Edite `sonar.organization` e `sonar.projectKey` no `pom.xml`.
4. No SonarCloud, desative **Automatic Analysis** (Administration → Analysis Method), já que a análise roda pelo CI.
5. Gere um token (My Account → Security) e crie o secret `SONAR_TOKEN` no repositório (Settings → Secrets and variables → Actions).
6. Faça push na `main`: o workflow `.github/workflows/sonarcloud.yml` compila o projeto e envia a análise para o SonarCloud.

## Rodando localmente (opcional)

Requer JDK 17+ e Maven:

```bash
export SONAR_TOKEN=seu_token
mvn verify sonar:sonar
```
