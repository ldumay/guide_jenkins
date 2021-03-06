# Guide Jenkins

Ceci est un guide pour Jenkins.


## 1 - Démarrer un Job à distance

Pour ce faire, il est nécessaire d'avoir :

- `un compte utilisateur avec un token`
- `un job avec un token`.

Vous devriez avoir, un ensemble de données tel que :

```
- User_Id : admin
- User_Token : 11566685c440ffc78ab15edb0527a37a6a (générer par Jenkins)
- Job_Id : demo
- Job_Token : 11ef1b80dea446767
```

> NB : Les données ci-dessous sont factices et peuvent être réutiliser pour des essais via un jenkins de démonstration dans un docker. Cela fut mon installation d'essai.

### 1.1 - Démarrer un Job à distance via `url`

```
http://localhost:8888/jenkins/buildByToken/buildWithParameters?job=demo&token=11ef1b80dea446767
```

```
https://localhost:8888/jenkins/job/demo/build?token=11ef1b80dea446767
```

```
https://localhost:8888/jenkins/buildWithParameters?token=11ef1b80dea446767&nom=test
```

### 1.2 - Démarrer un Job à distance via `curl`

### 1.2.1

```
curl -I -u admin:11566685c440ffc78ab15edb0527a37a6a "http://localhost:8888/job/demo/build?token=11ef1b80dea446767"
```

### 1.2.2

```
curl http://localhost:8888/job/demo/11ef1b80dea446767 \
  --user admin:11566685c440ffc78ab15edb0527a37a6a \
  --data id=123 --data verbosity=high
```






## Compilation depuis le terminal

Éléments nécessaire :

```
user_id = ldumay
user_token = 1139e012dea0d0a58820d707960c24c2bd
job_token = 5Wye5sQ9r7U89cAj8uPD
```

Commande :

```
curl -I -u <user_id>:<user_token> "http://<url_host>/job/<job_name>/build?token=<job_token>"
```

Résultat :

```
curl -I -u ldumay:1139e012dea0d0a58820d707960c24c2bd "http://ldumay.dev:8080/jenkins/job/Demo/build?token=5Wye5sQ9r7U89cAj8uPD"

HTTP/1.1 201 Created
Date: Fri, 11 Feb 2022 16:51:19 GMT
X-Content-Type-Options: nosniff
Location: http://ldumay.dev:8080/jenkins/queue/item/5/
Content-Length: 0
Server: Jetty(9.4.43.v20210629)
```

---

```
curl -I -u ldumay:1139e012dea0d0a58820d707960c24c2bd "https://ldumay.dev/jenkins/job/Demo/rssAll"  
```

## Compilation depuis une url

Fonctionne depuis une url :

```
https://ldumay.dev/jenkins/job/Demo/build?token=5Wye5sQ9r7U89cAj8uPD
```

> Génère un fichier build

## Compilation avec des paramètres

```
http://ldumay.dev:8080/jenkins/buildByToken/buildWithParameters?job=Demo&token=5Wye5sQ9r7U89cAj8uPD
```



---
---

### CrumbIssuer

`http://localhost:8080/crumbIssuer/api/json`

```
{
_class: "hudson.security.csrf.DefaultCrumbIssuer",
crumb: "ab25370113c79530ddd9b5ba7f3393bbb05913ee6a9511315e221c164409d198",
crumbRequestField: "Jenkins-Crumb"
}
```
