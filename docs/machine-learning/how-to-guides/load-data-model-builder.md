---
title: Charger les données d’apprentissage pour le générateur de modèles
description: Découvrez comment charger des données d’apprentissage à partir d’une base de données SQL Server ou d’un fichier pour les utiliser dans l’un des scénarios de générateur de modèles pour ML.NET.
ms.date: 10/29/2019
author: luisquintanilla
ms.author: luquinta
ms.custom: mvc, how-to, mlnet-tooling
ms.openlocfilehash: 64e366b3c66427ccd2810324abeb880f6cb9ebc1
ms.sourcegitcommit: cdb295dd1db589ce5169ac9ff096f01fd0c2da9d
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 06/09/2020
ms.locfileid: "84602204"
---
# <a name="load-training-data-into-model-builder"></a>Charger les données d’apprentissage dans le générateur de modèles

Découvrez comment charger vos jeux de données d’apprentissage à partir d’un fichier ou d’une base de données SQL Server pour une utilisation dans l’un des scénarios de générateur de modèles pour ML.NET. Les scénarios de générateur de modèles peuvent utiliser des SQL Server des bases de données, des fichiers image et des formats de fichier CSV ou TSV en tant que données d’apprentissage.

## <a name="training-dataset-limitations-in-model-builder"></a>Limitations des jeux de données de formation dans le générateur de modèles

Le générateur de modèles limite la quantité et le type de données que vous pouvez utiliser pour les modèles d’apprentissage :

- SQL Server données : 100 000 lignes
- Fichiers CSV et TSV : aucune limite de taille
- Images : PNG et JPG uniquement.

## <a name="model-builder-scenarios"></a>Scénarios de générateur de modèles

Le générateur de modèles vous permet de créer des modèles pour les scénarios de Machine Learning suivants :

- Analyse des sentiments (classification binaire) : classifier les données textuelles en deux catégories.
- Classification des problèmes (classification multiclasse) : classifier les données textuelles en 3 catégories ou plus.
- Prédiction de prix (régression) : prédire une valeur numérique.
- Classification des images (apprentissage profond) : classer les images en fonction des caractéristiques.
- Scénario personnalisé : créez des scénarios personnalisés à partir de vos données à l’aide de la régression, de la classification et d’autres tâches.

Cet article traite des scénarios de classification et de régression avec des données textuelles ou numériques, ainsi que des scénarios de classification d’images.

## <a name="load-text-or-numeric-data-from-a-file"></a>Charger du texte ou des données numériques à partir d’un fichier

Vous pouvez charger du texte ou des données numériques d’un fichier dans le générateur de modèles. Il accepte les formats de fichiers CSV (délimité par des virgules) ou TSV (délimité par des tabulations).

1. À l’étape données du générateur de modèles, sélectionnez **fichier** dans la liste déroulante source de données.
2. Sélectionnez le bouton en regard de la zone de texte **Sélectionner un fichier** , puis utilisez l’Explorateur de fichiers pour parcourir et sélectionner le fichier de données.
3. Choisissez une catégorie dans la liste déroulante **colonne à prédire (étiquette)** .
4. Dans la liste déroulante **colonnes d’entrée (fonctionnalités)** , vérifiez que les colonnes de données que vous souhaitez inclure sont cochées.

Vous avez terminé la configuration de votre fichier de source de données pour le générateur de modèles. Sélectionnez le lien **train** pour passer à l’étape suivante dans le générateur de modèles.

## <a name="load-data-from-a-sql-server-database"></a>Charger des données à partir d’une base de données SQL Server

Le générateur de modèles prend en charge le chargement de données à partir de bases de données locales et distantes SQL Server.

Pour charger des données à partir d’une base de données SQL Server dans module Builder :

1. À l’étape données du générateur de modèles, sélectionnez **SQL Server** dans la liste déroulante source de données.
1. Sélectionnez le bouton en regard de la zone **de texte connexion à SQL Server base de données** .
    1. Dans la boîte de dialogue **choisir des données** , sélectionnez **Microsoft SQL Server fichier de base de données**.
    1. Décochez la case **toujours utiliser cette sélection** et sélectionnez **Continuer**
    1. Dans la boîte de dialogue **Propriétés de connexion** , sélectionnez **Parcourir** et sélectionnez le téléchargé. Fichier MDF.
    1. Sélectionnez **OK**.
1. Choisissez le nom du DataSet dans la liste déroulante nom de la **table** .
1. Dans la liste déroulante **colonne à prédire (étiquette)** , choisissez la catégorie de données sur laquelle vous souhaitez effectuer une prédiction.
1. Dans la liste déroulante **colonnes d’entrée (fonctionnalités)** , vérifiez que les colonnes que vous souhaitez inclure sont cochées.

Vous avez terminé la configuration de votre fichier de source de données pour le générateur de modèles. Sélectionnez le lien **train** pour passer à l’étape suivante dans le générateur de modèles.

## <a name="set-up-image-data-files"></a>Configurer des fichiers de données image

Le générateur de modèles s’attend à ce que les données de l’image soient des fichiers JPG ou PNG organisés dans des dossiers qui correspondent aux catégories de la classification.

Pour charger des images dans le générateur de modèles, indiquez le chemin d’accès à un répertoire de niveau supérieur unique :

- Ce répertoire de niveau supérieur contient un sous-dossier pour chacune des catégories à prédire.
- Chaque sous-dossier contient les fichiers image appartenant à sa catégorie.

Dans la structure de dossiers illustrée ci-dessous, le répertoire de niveau supérieur est *flower_photos*. Il y a cinq sous-répertoires correspondant aux catégories que vous souhaitez prédire : marguerites, dandelion, roses, tournesols et tulipes. Chacun de ces sous-répertoires contient des images appartenant à sa catégorie respective.

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

Suivez ces didacticiels pour créer des applications Machine Learning avec le générateur de modèles :

- [Prédire des prix à l’aide de la régression](../tutorials/predict-prices-with-model-builder.md)
- [Analyser les sentiments dans une application Web à l’aide de la classification binaire](../tutorials/sentiment-analysis-model-builder.md)

Si vous effectuez l’apprentissage d’un modèle à l’aide de code, [Découvrez comment charger des données à l’aide de l’API ml.net](load-data-ml-net.md).
