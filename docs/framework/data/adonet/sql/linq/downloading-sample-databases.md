---
title: Obtenez les bases de données SQL Server pour ADO.NET échantillons de code
description: Téléchargez les données de données SQL Server utilisées dans les échantillons de code dans la documentation ADO.NET, ainsi que le serveur SQL et les outils de gestion
ms.date: 01/11/2019
ms.assetid: ef9d69a1-9461-43fe-94bb-7c836754bcb5
ms.openlocfilehash: 3449f502834f449f5023bd52457d45ffaf9b0fa1
ms.sourcegitcommit: d9470d8b2278b33108332c05224d86049cb9484b
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 04/17/2020
ms.locfileid: "81607982"
---
# <a name="get-the-sample-databases-for-adonet-code-samples"></a>Obtenez les bases de données d’échantillons pour les échantillons de code ADO.NET

Un certain nombre d’exemples et [!INCLUDE[vbtecdlinq](../../../../../../includes/vbtecdlinq-md.md)] de procédures pas à pas dans la documentation utilisent des bases de données SQL Server et SQL Server Express. Vous pouvez télécharger ces produits gratuitement à partir de Microsoft.

## <a name="get-the-northwind-sample-database-for-sql-server"></a>Obtenez la base de données de l’échantillon Northwind pour SQL Server

Téléchargez `instnwnd.sql` le script à partir du référentiel GitHub suivant pour créer et charger la base de données de l’échantillon Northwind pour SQL Server :

[Northwind et pubs échantillonnent des bases de données pour Microsoft SQL Server](https://github.com/Microsoft/sql-server-samples/tree/master/samples/databases/northwind-pubs)

Avant de pouvoir utiliser la base de données `instnwnd.sql` Northwind, vous devez exécuter le fichier de script téléchargé pour recréer la base de données sur une instance de SQL Server en utilisant [SQL Server Management Studio](#get_ssms) ou un outil similaire. Suivez les instructions dans le fichier Readme dans le référentiel.

> [!TIP]
> Si vous êtes à la recherche de la base de données Northwind pour Microsoft Access, consultez [la base de données de l’échantillon Northwind pour Microsoft Access](#northwind_access).

## <a name="get-the-northwind-sample-database-for-microsoft-access"></a><a name="northwind_access"></a>Obtenez la base de données de l’échantillon Northwind pour Microsoft Access

La base de données d’échantillons Northwind pour Microsoft Access n’est pas disponible sur le Microsoft Download Center. Pour installer Northwind directement à partir de l’intérieur d’Access, faites les choses suivantes :

1. Accès libre.

1. Entrez **Northwind** dans la **boîte De modèles en ligne,** puis **sélectionnez Entrez**.

1. Sur l’écran des résultats, sélectionnez **Northwind**. Une nouvelle fenêtre s’ouvre sur une description de la base de données Northwind.

1. Dans la nouvelle fenêtre, dans la boîte de texte **Nom de fichier,** fournissez un nom de fichier pour votre copie de la base de données Northwind.

1. Sélectionnez **Create** (Créer). Access télécharge la base de données Northwind et prépare le fichier.

1. Lorsque ce processus est terminé, la base de données s’ouvre avec un écran Bienvenue.

## <a name="get-the-adventureworks-sample-database-for-sql-server"></a>Obtenez la base de données d’échantillons AdventureWorks pour SQL Server

Téléchargez la base de données de l’échantillon AdventureWorks pour SQL Server à partir du référentiel GitHub suivant :

[Exemples de bases de données AdventureWorks](https://github.com/Microsoft/sql-server-samples/releases/tag/adventureworks)

Après avoir téléchargé l’un\*des fichiers de sauvegarde de base de données (.bak), redérez la sauvegarde à une instance de SQL Server en utilisant SQL Server Management Studio (SSMS). Voir [Get SQL Server Management Studio](#get_ssms).

## <a name="get-sql-server-management-studio"></a><a name="get_ssms"></a>Obtenez SQL Server Management Studio
Si vous souhaitez afficher ou modifier une base de données que vous avez téléchargée, vous pouvez utiliser SQL Server Management Studio (SSMS). Télécharger SSMS à partir de la page suivante:

[Télécharger SQL Server Management Studio (SSMS)](/sql/ssms/download-sql-server-management-studio-ssms)

Vous pouvez également afficher et gérer des bases de données dans l’environnement de développement intégré Visual Studio (IDE). Dans [Visual Studio](https://www.visualstudio.com/downloads/?utm_medium=microsoft&utm_source=docs.microsoft.com&utm_campaign=button+cta&utm_content=download+vs2019), connectez-vous à la base de données de **SQL Server Object Explorer**, ou créez une connexion de données à la base de données dans Server **Explorer**. Ouvrez ces volets explorateurs à partir du menu **View.**

## <a name="get-sql-server-express"></a><a name="get_sql"></a>Obtenez SQL Server Express

SQL Server Express est une édition gratuite d’entrée de gamme de SQL Server que vous pouvez redistribuer avec des applications. Télécharger SQL Server Express à partir de la page suivante:
  
[SQL Server Express](https://www.microsoft.com/sql-server/sql-server-editions-express)

Si vous utilisez [Visual Studio](https://www.visualstudio.com/downloads/?utm_medium=microsoft&utm_source=docs.microsoft.com&utm_campaign=button+cta&utm_content=download+vs2019), SQL Server Express LocalDB est inclus dans l’édition communautaire gratuite de Visual Studio, ainsi que les éditions Professionnelles et Supérieures.  

## <a name="see-also"></a>Voir aussi

- [Prise en main](getting-started.md)
