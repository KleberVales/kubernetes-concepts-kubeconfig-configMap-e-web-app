# 🌐 Kubernetes Concepts: kubeconfig, ConfigMap e Web App

Este repositório explica três conceitos fundamentais usados em ambientes Kubernetes e aplicações web modernas: **kubeconfig**, **ConfigMap** e **Web App**.  
Esses elementos são essenciais para configurar, gerenciar e implantar aplicações em clusters de forma segura e organizada.

---

## ⚙️ kubeconfig

O **kubeconfig** é um **arquivo de configuração** usado pelo **kubectl** (CLI do Kubernetes) para se conectar e autenticar em um **cluster Kubernetes**.

### 🔍 O que ele faz:

- Define **as credenciais** para acesso (usuário, token, certificados).
- Armazena **endereços de clusters** e **contextos** (qual cluster e namespace usar).
- Permite **trocar entre múltiplos clusters** sem precisar reconfigurar o acesso.

### 🧩 Estrutura básica:

```yaml
apiVersion: v1
kind: Config
clusters:
- name: my-cluster
  cluster:
    server: https://<api-server-endpoint>
    certificate-authority-data: <CA_DATA>
users:
- name: my-user
  user:
    token: <ACCESS_TOKEN>
contexts:
- name: my-context
  context:
    cluster: my-cluster
    user: my-user
current-context: my-context

```

## 🛠️ Local padrão:

- Linux/Mac: ~/.kube/config
- Windows: %USERPROFILE%\.kube\config

## 🧱 ConfigMap

O ConfigMap é um objeto do Kubernetes usado para armazenar dados de configuração em pares chave: valor.

### 🔍 Para que serve:

Ele permite separar as configurações da imagem da aplicação, evitando precisar reconstruir o contêiner sempre que algo mudar.

🧩 Exemplo:
```yaml
apiVersion: v1
kind: ConfigMap
metadata:
  name: app-config
data:
  DATABASE_URL: "jdbc:mysql://mysql-service:3306/appdb"
  APP_MODE: "production"
```






