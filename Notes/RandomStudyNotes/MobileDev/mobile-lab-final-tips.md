1) entity annotations
2) DAO classes
3) Database class
4) Database provider
5) Repo (calling Dio and DAO functions)
6) run this command:
```sh
flutter packages pub run build_runner
```
6) make providers for entities
7) database view in `model` directory
8) call `StreamBuilder` in screen for the database view
```
screen <- provider <- repo <- dao <- view (entity)
```
## to check mobile db file
```
view -> tool windows -> device explorer -> projectname -> data -> .db
```
## to open `.db` file using `sqlite3`
```sh
sqlite3 data.db
```
