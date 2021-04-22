# Hashicorp Vault Secrets Plugin

Enables the use of vault secrets from within a pipeline.

### Build
Java 8
```
mvn verify -e -Duse-jenkins-bom
```

### Dependencies
- [hashicorp-vault-plugin](https://github.com/jenkinsci/hashicorp-vault-plugin) Supports from 3.x.x version

- [credentials-plugin](https://github.com/jenkinsci/credentials-plugin)

### Examples

##### Using global vault configuration

```
pipeline {
    agent any
    environment {
        SECRET = vault path: 'secrets', key: 'username'
    }
    stages {
        stage("read vault key") {
            steps {
                echo "${SECRET}"
            }
        }
    }
}
```

##### Using pipeline specific configuration

```
pipeline {
    agent any
    environment {
        SECRET = vault path: 'secrets', key: 'username', vaultUrl: 'https://my-vault.com:8200', credentialsId: 'my-creds', engineVersion: "2"
    }
    stages {
        stage("read vault key") {
            steps {
                echo "${SECRET}"
            }
        }
    }
}
```
