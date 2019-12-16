# OccazMalin
> Le site de petites annonces...


## Entités

### Users

- id                            : uuid          : char(36)
- email                         : string 180    : varchar(180)
- password                      : string 255    : varchar(255)
- roles                         : json          : longtext/json
- firstname                     : string 40     : varchar(40)
- lastname                      : string 40     : varchar(40)
- screenname                    : string 40     : varchar(40)
- phone                         : string 20     : varchar(20)
- birthday                      : datetime      : datetime
- language                      : string 2      : char(2)
- isActive                      : boolean       : tinyint(1)
- activationToken               : string 255    : varchar(255)
- passwordToken                 : string 255    : varchar(255)
- passwordTokenExpiration       : datetime      : datetime
- picture                       : ManyToOne     : int(11)
- address                       : ManyToOne     : int(11)

### Ads 

- id                            : uuid          : char(36)
- title                         : string 90     : varchar(90)
- price                         : decimal 10,2  : decimal(10,2)
- description                   : text          : longtext
- language                      : string 2      : char(2)
- state                         : string xxx    : enum('new','used','broken')
- date_publish                  : datetime      : datetime
- date_expire                   : datetime      : datetime
- createdBy                     : ManyToOne     : char(36)
- category                      : ManyToOne     : int(11)
- location                      : ManyToOne     : int(11)
- attachments                   : OneToMany     : int(11)

### Favorites

- user                          : ManyToOne     : char(36)
- ad                            : ManyToOne     : char(36)

### Categories

- id                            :               : int(11)
- name                          : string 30     : varchar(30)
- slug                          : string 30     : varchar(30)
- color                         : string 7      : char(7)

### Offers

- id                            :               : int(11)
- user                          : ManyToOne     : char(36)
- ad                            : ManyToOne     : char(36)
- price                         : decimal 10,2  : decimal(10,2)
- message                       : text          : text
- offerDate                     : datetime      : datetime

### Medias

- id                            :               : int(11)
- type                          : string xxx    : enum('image','video','sound')
- path                          : string 40     : varchar(40)
- user                          : ManyToOne     : char(36)

### Attachements

- id                            :               : int(11)
- media                         : ManyToOne     : char(36)
- ad                            : ManyToOne     : char(36)
- title                         : string 80     : varchar(80)

### Addresses

- id                            :               : int(11)
- address                       : string 255    : varchar(255)
- additional                    : string 255    : varchar(255)
- postalcode                    : string 10     : varchar(10)
- city                          : string 80     : varchar(80)
- region                        : string 80     : varchar(80)
- country                       : string 2      : char(2)





## Router

Homepage :              /
Ads :                   /
Ads (by category) :     /?categ=categ-slug
Ads (by user) :         /?user=xxxxxx
Create Ad :             /ad
Ad details :            /ad/{id}
Ad edit :               /ad/{id}/edit
Ad delete :             /ad/{id}/delete
Add ad to favorites :   /ad/{id}/favorites

Login :                 /login
Registration :          /register
Account activation :    /activate?token=xxxxxxx
Lost Password :         /forgotten-password
Reset Password :        /reset-password?token=xxxxxxx
Renew Password :        /renew-password
User profile/account :  /account
User ads :              /my-ads
User favorites :        /favorites

Terms :                 /legal
Contact :               /contact


## Installation du projet

### Installation de la base Symfony

```bash
composer create-project symfony/skeleton <my-project> "4.4.*"
cd <my-project>
```

### Installation des dépendances

#### Installation des dépendances Back

```bash
composer require symfony/web-server-bundle --dev
composer require symfony/maker-bundle --dev
composer require doctrine/doctrine-fixtures-bundle --dev 
composer require profiler --dev
composer require symfony/orm-pack
composer require annotations
composer require form
composer require validator
composer require twig-bundle
composer require security-csrf
composer require symfony/swiftmailer-bundle
composer require security
composer require symfony/translation
composer require encore
composer require claviska/simpleimage
composer require cocur/slugify
composer require ramsey/uuid-doctrine

composer require symfony/flex
composer require symfony/console
composer require symfony/dotenv
composer require symfony/framework-bundle
composer require symfony/yaml
```

#### Installation des dépendances Front

```bash
npm install bootstrap
npm install jquery
npm install popper.js
```

### Mise en place de l'environnement VSCode

1. Ouverture du répertoire **my-project** en mode projet sur VSCode.
2. Configuration de Debugger For Chrome

### Test du serveur de développement

```bash
php bin/console server:run *:8004
```


### Création de la copie `.env.dist`

Pour Unix :

```bash
cp .env .env.dist
```

Pour Windows :

```bash
copy .env .env.dist
```


### Initialisation de GIT

#### Initialisation de GIT

```bash
git init
```

#### Ignorer les fichiers pour GIT

Dans le fichier `.gitignore`, ajouter :
- `.env`


#### Préparer le remote (GitHub)

1. Identifiez-vous sur https://github.com/
2. Créez nouveau dépôt
    - renseigner le Nom
    - renseigner la Description
    - dépôt public
3. Créez le premier commit
    - `git checkout -b develop`
    - `git add *`
    - `git add .env.dist`
    - `git add .gitignore`
    - `git commit -m 'initial commit'`
    - `git remote add origin https://github.com/<USER>/<repository>.git`
    - `git push --set-upstream origin develop`
