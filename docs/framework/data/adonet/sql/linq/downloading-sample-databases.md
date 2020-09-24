---
title: Obtenir l’exemple de base de données SQL Server pour les exemples de code ADO.NET
description: Téléchargez l’exemple de bases de données SQL Server utilisées dans les exemples de code dans la documentation ADO.NET, ainsi que les SQL Server et les outils de gestion
ms.date: 01/11/2019
ms.assetid: ef9d69a1-9461-43fe-94bb-7c836754bcb5
ms.openlocfilehash: f7c0d1eb0089a6bfabc92e1deecf563c3e59cc6a
ms.sourcegitcommit: 5b475c1855b32cf78d2d1bbb4295e4c236f39464
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 09/24/2020
ms.locfileid: "91156054"
---
# <a name="get-the-sample-databases-for-adonet-code-samples"></a>Obtenir les exemples de bases de données pour les exemples de code ADO.NET

Un certain nombre d’exemples et de procédures pas à pas de la [!INCLUDE[vbtecdlinq](../../../../../../includes/vbtecdlinq-md.md)] documentation utilisent des exemples SQL Server des bases de données et des SQL Server Express. Vous pouvez télécharger ces produits gratuitement auprès de Microsoft.

## <a name="get-the-northwind-sample-database-for-sql-server"></a>Obtenir l’exemple de base de données Northwind pour SQL Server

Téléchargez le script `instnwnd.sql` à partir du référentiel GitHub suivant pour créer et charger l’exemple de base de données Northwind pour SQL Server :

[Exemples de bases de données Northwind et pubs pour Microsoft SQL Server](https://github.com/Microsoft/sql-server-samples/tree/master/samples/databases/northwind-pubs)

Avant de pouvoir utiliser la base de données Northwind, vous devez exécuter le `instnwnd.sql` fichier de script téléchargé pour recréer la base de données sur une instance de SQL Server à l’aide de [SQL Server Management Studio](#get_ssms) ou d’un outil similaire. Suivez les instructions du fichier Lisez-moi dans le référentiel.

> [!TIP]
> Si vous recherchez la base de données Northwind pour Microsoft Access, consultez [installer l’exemple de base de données Northwind pour Microsoft Access](#northwind_access).

## <a name="get-the-northwind-sample-database-for-microsoft-access"></a><a name="northwind_access"></a> Obtenir l’exemple de base de données Northwind pour Microsoft Access

L’exemple de base de données Northwind pour Microsoft Access n’est pas disponible dans le centre de téléchargement Microsoft. Pour installer Northwind directement à partir d’Access, procédez comme suit :

1. Ouvrez Access.

1. Entrez **Northwind** dans la zone **Rechercher des modèles en ligne** , puis sélectionnez **entrée**.

1. Dans l’écran résultats, sélectionnez **Northwind**. Une nouvelle fenêtre s’ouvre avec une description de la base de données Northwind.

1. Dans la nouvelle fenêtre, dans la zone de texte **nom de fichier** , fournissez un nom de fichier pour votre copie de la base de données Northwind.

1. Sélectionnez **Create** (Créer). Access télécharge la base de données Northwind et prépare le fichier.

1. Une fois ce processus terminé, la base de données s’ouvre avec un écran d’accueil.

## <a name="get-the-adventureworks-sample-database-for-sql-server"></a>Obtenir l’exemple de base de données AdventureWorks pour SQL Server

Téléchargez l’exemple de base de données AdventureWorks pour SQL Server à partir du dépôt GitHub suivant :

[Exemples de bases de données AdventureWorks](https://github.com/Microsoft/sql-server-samples/releases/tag/adventureworks)

Après avoir téléchargé l’un des fichiers de sauvegarde de base de données ( \* . bak), restaurez la sauvegarde sur une instance de SQL Server à l’aide de SQL Server Management Studio (SSMS). Consultez [obtenir des SQL Server Management Studio](#get_ssms).

## <a name="get-sql-server-management-studio"></a><a name="get_ssms"></a> Recevoir SQL Server Management Studio

Si vous souhaitez afficher ou modifier une base de données que vous avez téléchargée, vous pouvez utiliser SQL Server Management Studio (SSMS). Téléchargez SSMS à partir de la page suivante :

[Télécharger SQL Server Management Studio (SSMS)](/sql/ssms/download-sql-server-management-studio-ssms)

Vous pouvez également afficher et gérer des bases de données dans l’environnement de développement intégré (IDE) de Visual Studio. Dans [Visual Studio](https://www.visualstudio.com/downloads/?utm_medium=microsoft&utm_source=docs.microsoft.com&utm_campaign=button+cta&utm_content=download+vs2019), connectez-vous à la base de données à partir de **Explorateur d’objets SQL Server**ou créez une connexion de données à la base de données dans **Explorateur de serveurs**. Ouvrez ces volets Explorateur dans le menu **affichage** .

## <a name="get-sql-server-express"></a><a name="get_sql"></a> Recevoir SQL Server Express

SQL Server Express est une édition gratuite de SQL Server que vous pouvez redistribuer avec les applications. Téléchargez SQL Server Express à partir de la page suivante :
  
[SQL Server Express](https://www.microsoft.com/sql-server/sql-server-editions-express)

Si vous utilisez [Visual Studio](https://www.visualstudio.com/downloads/?utm_medium=microsoft&utm_source=docs.microsoft.com&utm_campaign=button+cta&utm_content=download+vs2019), SQL Server Express la base de données locale est incluse dans l’édition Community gratuite de Visual Studio, ainsi que dans les éditions Professional et supérieures.  

## <a name="see-also"></a>Voir aussi

- [Prise en main](getting-started.md)
