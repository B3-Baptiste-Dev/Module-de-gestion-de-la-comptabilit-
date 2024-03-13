# Module-de-gestion-de-la-comptabilit-

# Dictionnaire de données

| Nom                   | Type         | Description                                         |
|-----------------------|--------------|-----------------------------------------------------|
| ID_Compte             | INT          | Identifiant unique pour chaque compte               |
| Nom_Compte            | VARCHAR(255) | Nom du compte (ex : "Fournisseurs", "Clients")      |
| Solde                 | DECIMAL      | Solde actuel du compte                              |
| Date_Ouverture        | DATE         | Date d'ouverture du compte                          |
| ID_Transaction        | INT          | Identifiant unique pour chaque transaction          |
| Date_Transaction      | DATE         | Date à laquelle la transaction a été réalisée       |
| Montant               | DECIMAL      | Montant de la transaction                           |
| Type_Transaction      | VARCHAR(50)  | Type de la transaction (ex : "Crédit", "Débit")     |
| ID_Utilisateur        | INT          | Identifiant unique pour chaque utilisateur          |
| Nom_Utilisateur       | VARCHAR(255) | Nom de l'utilisateur                                |
| Role_Utilisateur      | VARCHAR(100) | Rôle de l'utilisateur (ex : "Administrateur", "User") |


# Modèle Conceptuel de Données (MCD)

![MCD](lien_vers_l'image_du_MCD.png)

- Compte(ID_Compte, Nom_Compte, Solde, Date_Ouverture)
- Transaction(ID_Transaction, Date_Transaction, Montant, Type_Transaction, ID_Compte)
- Utilisateur(ID_Utilisateur, Nom_Utilisateur, Role_Utilisateur)

Associations:
- Un Compte peut avoir plusieurs Transactions
- Un Utilisateur peut réaliser plusieurs Transactions

# Modèle Logique de Données (MLD)

- Compte(ID_Compte PK, Nom_Compte, Solde, Date_Ouverture)
- Transaction(ID_Transaction PK, Date_Transaction, Montant, Type_Transaction, ID_Compte FK)
- Utilisateur(ID_Utilisateur PK, Nom_Utilisateur, Role_Utilisateur)


# Modèle Physique de Données (MPD)

```sql
CREATE TABLE Compte (
    ID_Compte INT PRIMARY KEY,
    Nom_Compte VARCHAR(255),
    Solde DECIMAL(10, 2),
    Date_Ouverture DATE
);

CREATE TABLE Transaction (
    ID_Transaction INT PRIMARY KEY,
    Date_Transaction DATE,
    Montant DECIMAL(10, 2),
    Type_Transaction VARCHAR(50),
    ID_Compte INT,
    FOREIGN KEY (ID_Compte) REFERENCES Compte(ID_Compte)
);

CREATE TABLE Utilisateur (
    ID_Utilisateur INT PRIMARY KEY,
    Nom_Utilisateur VARCHAR(255),
    Role_Utilisateur VARCHAR(100)
);
```

