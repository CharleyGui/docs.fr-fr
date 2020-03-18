---
title: Données de formation de charge pour Model Builder
description: Découvrez comment charger les données de formation à partir d’une base de données SQL Server ou d’un fichier à utiliser dans l’un des scénarios Model Builder pour ML.NET.
ms.date: 10/29/2019
author: luisquintanilla
ms.author: luquinta
ms.custom: mvc, how-to, mlnet-tooling
ms.openlocfilehash: 23de2d06090f4c1eaa2c79178ba4c346698d45e1
ms.sourcegitcommit: 7588136e355e10cbc2582f389c90c127363c02a5
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 03/15/2020
ms.locfileid: "78849157"
---
# <a name="load-training-data-into-model-builder"></a>Charger les données de formation dans Model Builder

Découvrez comment charger vos jeux de données de formation à partir d’un fichier ou d’une base de données SQL Server pour une utilisation dans l’un des scénarios Model Builder pour ML.NET. Les scénarios Model Builder peuvent utiliser les bases de données SQL Server, les fichiers d’images et les formats de fichiers CSV ou TSV comme données de formation.

## <a name="training-dataset-limitations-in-model-builder"></a>Limitations de jeu de données de formation dans Le constructeur modèle

Modèle Builder limite la quantité et le type de données que vous pouvez utiliser pour les modèles de formation :

- Données SQL Server : 100 000 lignes
- Fichiers CSV et TSV : aucune limite de taille
- Images: PNG et JPG seulement.

## <a name="model-builder-scenarios"></a>Scénarios De constructeur de modèles

Model Builder vous aide à créer des modèles pour les scénarios d’apprentissage automatique suivants :

- Analyse du sentiment (classification binaire) : Classer les données textuelles en deux catégories.
- Classification des questions (classification multiclasse) : Classer les données textuelles en 3 catégories ou plus.
- Prévision des prix (régression) : Prédire une valeur numérique.
- Classification des images (apprentissage profond) : Catégoriser les images en fonction des caractéristiques.
- Scénario personnalisé : Construisez des scénarios personnalisés à partir de vos données à l’aide de la régression, de la classification et d’autres tâches.

Cet article couvre les scénarios de classification et de régression avec des données textuelles ou numériques, ainsi que des scénarios de classification d’images.

## <a name="load-text-or-numeric-data-from-a-file"></a>Charger le texte ou les données numériques d’un fichier

Vous pouvez charger des données textuelles ou numériques à partir d’un fichier dans Model Builder. Il accepte les formats de fichiers délimités par virgule (CSV) ou délimités par onglet (TSV).

1. Dans l’étape de données de Model Builder, sélectionnez **Fichier** à partir de la baisse de la source de données.
2. Sélectionnez le bouton à côté de la boîte de texte **Select,** et utilisez File Explorer pour parcourir et sélectionner le fichier de données.
3. Choisissez une catégorie dans la **colonne pour prédire (label)** dropdown.
4. À partir du décrochage **des colonnes d’entrée (Caractéristiques),** confirmez que les colonnes de données que vous souhaitez inclure sont vérifiées.

Vous avez terminé la mise en place de votre fichier source de données pour Model Builder. Sélectionnez le lien **Train** pour passer à l’étape suivante dans Model Builder.

## <a name="load-data-from-a-sql-server-database"></a>Chargez les données d’une base de données SQL Server

Model Builder prend en charge le chargement des données des bases de données LOCALEs et éloignées DE SQL Server.

Pour charger les données d’une base de données SQL Server dans Module Builder :

1. Dans l’étape de données de Model Builder, sélectionnez **SQL Server** à partir de la source de données.
1. Sélectionnez le bouton à côté de la boîte **texte de base de données Connect to SQL Server.**
    1. Dans le dialogue **Choisissez les données,** sélectionnez **Microsoft SQL Server Database File**.
    1. Décochez **la toujours utiliser cette** boîte à cocher de sélection et sélectionnez **Continuer**
    1. Dans le dialogue **Connection Properties,** **sélectionnez Browse** et sélectionnez les téléchargements . Fichier MDF.
    1. Sélectionnez **OK**.
1. Choisissez le nom de jeu de données de la décroche du nom de **table.**
1. De la **colonne à prédire (label)** dropdown, choisissez la catégorie de données sur laquelle vous souhaitez faire une prédiction.
1. À partir du décrochage **des colonnes d’entrée (Caractéristiques),** confirmez les colonnes que vous souhaitez inclure sont vérifiées.

Vous avez terminé la mise en place de votre fichier source de données pour Model Builder. Sélectionnez le lien **Train** pour passer à l’étape suivante dans Model Builder.

## <a name="set-up-image-data-files"></a>Configurer des fichiers de données d’image

Model Builder s’attend à ce que les données d’image soient des fichiers JPG ou PNG organisés dans des dossiers correspondant aux catégories de la classification.

Pour charger des images dans Model Builder, offrez le chemin vers un répertoire de haut niveau unique :

- Ce répertoire de haut niveau contient un sous-pli pour chacune des catégories à prévoir.
- Chaque sous-pliage contient les fichiers d’image appartenant à sa catégorie.

Dans la structure du dossier illustrée ci-dessous, le répertoire de haut niveau est *flower_photos*. Il y a cinq sous-directeurs correspondant aux catégories que vous voulez prédire : marguerite, pissenlit, roses, tournesols et tulipes. Chacune de ces sous-directions contient des images appartenant à sa catégorie respective.

```text
\---flower_photos
    +---daisy
    |       100080576_f52e8ee070_n.jpg
    |       102841525_bd6628ae3c.jpg
    |       105806915_a9c13e2106_n.jpg
    |
    +---dandelion
    |       10443973_aeb97513fc_m.jpg
    |       10683189_bd6e371b97.jpg
    |       10919961_0af657c4e8.jpg
    |
    +---roses
    |       102501987_3cdb8e5394_n.jpg
    |       110472418_87b6a3aa98_m.jpg
    |       118974357_0faa23cce9_n.jpg
    |
    +---sunflowers
    |       127192624_afa3d9cb84.jpg
    |       145303599_2627e23815_n.jpg
    |       147804446_ef9244c8ce_m.jpg
    |
    \---tulips
            100930342_92e8746431_n.jpg
            107693873_86021ac4ea_n.jpg
            10791227_7168491604.jpg
```

## <a name="next-steps"></a>Étapes suivantes

Suivez ces tutoriels pour créer des applications d’apprentissage automatique avec Model Builder :

- [Prédire des prix à l’aide de la régression](../tutorials/predict-prices-with-model-builder.md)
- [Analyser le sentiment dans une application web à l’aide de la classification binaire](../tutorials/sentiment-analysis-model-builder.md )

Si vous entraînez un modèle à l’aide de code, [apprenez à charger des données à l’aide de l’API ML.NET](load-data-ml-net.md).
