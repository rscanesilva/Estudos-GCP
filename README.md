## Como criar um cluster do GKE pelo Cloud Shell

1) No Cloud Shell, digite o comando abaixo para definir a variável de ambiente da zona e o nome do cluster.

```
$ export my_zone=us-central1-a
$ export my_cluster=standard-cluster-1
```
2) No Cloud Shell, digite o comando abaixo para criar um cluster do Kubernetes.
```
$ gcloud container clusters create $my_cluster --num-nodes 3 --zone $my_zone --enable-ip-alias
```

## Como modificar um cluster via cloud shell
1) No Cloud Shell, execute o seguinte comando para que standard-cluster-1 passe a ter quatro nós:
```
$ gcloud container clusters resize $my_cluster --zone $my_zone --size=4
```

##Conectar-se ao cluster GKE e habilitar o kubectl
1) Execute o seguinte comando, que cria um arquivo kubeconfig com as credenciais do usuário atual para permitir a autenticação, além de indicar os detalhes do endpoint de um cluster específico para permitir a comunicação com esse cluster por meio da ferramenta de linha de comando kubectl:
```
$ gcloud container clusters get-credentials $my_cluster --zone $my_zone
```
Esse comando cria um diretório .kube no principal, se ainda não houver um. No diretório .kube, o comando cria um arquivo chamado config (caso ainda não exista). Ele será usado para armazenar as informações de autenticação e configuração. O arquivo de configuração é normalmente chamado kubeconfig, para visualizar o conteúdo do arquivo criado, execute o seguinte comando:
```
nano ~/.kube/config
```
