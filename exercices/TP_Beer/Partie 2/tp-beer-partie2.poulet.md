## 10 Listez pour chaque ticket la quantité totale d’articles vendus. (Classer par quantité décroissante)

```mysql
SELECT NUMERO_TICKET, SUM(QUANTITE) AS QUANTITE_TOTALE
FROM ventes
GROUP BY NUMERO_TICKET
ORDER BY QUANTITE_TOTALE DESC;
```

- Vous aurez besoin de la fonction `SUM`



## 11 Listez chaque ticket pour lequel la quantité totale d’articles vendus est supérieure à 500. (Classer par quantité décroissante)

```mysql
SELECT NUMERO_TICKET, SUM(QUANTITE) AS QUANTITE_TOTALE
FROM ventes
GROUP BY NUMERO_TICKET
HAVING QUANTITE_TOTALE > 500
ORDER BY QUANTITE_TOTALE DESC;
```

- Vous devrez utiliser la fonction `GROUP BY`
- Vous devrez utiliser `ORDER BY`

## 12 Listez chaque ticket pour lequel la quantité totale d’articles vendus est supérieure à 500. On exclura du total, les ventes ayant une quantité supérieure à 50 (classer par quantité décroissante)

```mysql
SELECT NUMERO_TICKET, SUM(QUANTITE) AS QUANTITE_TOTALE
FROM ventes
WHERE QUANTITE <= 50
GROUP BY NUMERO_TICKET
HAVING QUANTITE_TOTALE > 500
ORDER BY QUANTITE_TOTALE DESC;
```

- Vous réaliserez la somme des quantités vendues avec la fonction `SUM` dans le `SELECT`

## 13 Listez les bières de type ‘Trappiste’. (id, nom de la bière, volume et titrage)

```mysql
SELECT a.ID_ARTICLE , a.NOM_ARTICLE , a.VOLUME , a.TITRAGE
FROM article a
JOIN type t ON a.ID_TYPE  = t.ID_TYPE 
WHERE t.NOM_TYPE  = 'Trappiste';
```

- Vous devrez faire une jointure avec la table `type`

## 14 Listez les marques de bières du continent ‘Afrique’

```mysql
SELECT DISTINCT m.NOM_MARQUE 
FROM marque m
JOIN pays p ON m.ID_PAYS = p.ID_PAYS 
JOIN continent c ON p.ID_CONTINENT  = c.ID_CONTINENT
WHERE c.NOM_CONTINENT = 'Afrique';
```

- Vous devrez faire deux jointures

## 15 Lister les bières du continent ‘Afrique’

```mysql
SELECT a.ID_ARTICLE, a.NOM_ARTICLE, p.NOM_PAYS
FROM article a
JOIN marque m ON a.ID_MARQUE = m.ID_MARQUE
JOIN pays p ON m.ID_PAYS = p.ID_PAYS
JOIN continent c ON p.ID_CONTINENT = c.ID_CONTINENT
WHERE c.NOM_CONTINENT = 'Afrique';
```

- Vous devrez faire trois jointures

## 16. Lister les tickets (année, numéro de ticket, montant total payé). En sachant que le prix de vente est égal au prix d’achat augmenté de 15%.

```mysql
SELECT t.ANNEE, t.NUMERO_TICKET,
SUM(v.QUANTITE * a.PRIX_ACHAT * 1.15) AS MONTANT_TOTAL
FROM ticket t
JOIN ventes v USING(NUMERO_TICKET)
JOIN article a ON v.ID_ARTICLE = a.ID_ARTICLE 
GROUP BY t.ANNEE, t.NUMERO_TICKET
```

- Vous devrez faire un `SUM` sur la quantité multipliée par le prix d'achat, et ajouter 15% 
- Vous devrez faire deux jointures

> Vous aurez certainement besoin du mot `USING` dans votre requête.

## 17  Donner le C.A. par année.

```mysql
```

- Vous devrez faire la somme des quantités multipliées par le prix d'achat, et ajouter 15% au résultat (*1.15)

## 18. Lister les quantités vendues de chaque article pour l’année 2016.

```mysql

```

- Vous devrez faire une jointure

## 19. Lister les quantités vendues de chaque article pour les années 2014, 2015, 2016.

```mysql

```

- Vous devrez faire la somme des quantités vendues avec la fonction `SUM` dans le `SELECT`
