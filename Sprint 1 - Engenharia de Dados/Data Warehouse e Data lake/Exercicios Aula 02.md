# Mongo DB
### Q1: Pesquisa pelos tweets com número de likes maior ou igual a 10
```
 db.tweets.find({likes: {$gte: 10} })
```

### Q2: Inserção de 50 tweets, usando somente os usuários user1, user2 e user3, mas variando o texto e o número de likes, que pode ser um número qualquer entre 1 e 100;

```
const users = ['user1', 'user2', 'user3'];
const tweets = [];

for (let i = 1; i <= 50; i++) {
  tweets.push({
    user: users[Math.floor(Math.random() * users.length)],
    text: `Este é o tweet número ${i}`,
    likes: Math.floor(Math.random() * 100) + 1
  });
}

db.tweets.insertMany(tweets);
```

### Q3: Atualização de todos os tweets do user1, somando-se 5 ao número de likes correspondente;

```
db.tweets.updateMany({username: 'user1'},{$inc: {"like": 5}})
```

### Q4: Remoção de todos os tweets de user3 com número de likes menor que 10.

```
db.tweets.deleteMany({username: "user3", like: {$lt: 10}})
```

# Neo4j
### Q1: Contar a quantidade de tweets enviados por cada usuário:
```
MATCH (u:user)-[m:make]->()
RETURN u.name, count(u)
```
### Q2: Atualizar o número de likes de um tweet específico com base no 'id':
```
MATCH (t:tweet {id: 3})
SET t.likes = 500
```
### Q3: Recuperar todos os tweets com no mínimo 10 likes:
```
MATCH (t:tweet)
WHERE t.likes >= 10
RETURN t
```