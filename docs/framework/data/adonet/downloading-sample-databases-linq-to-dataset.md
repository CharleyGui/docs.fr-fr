---
title: Téléchargement d'exemples de base de données (LINQ to DataSet)
ms.date: 03/30/2017
ms.assetid: eb42a7af-d410-4b7f-b4a8-13c72ce6fd09
ms.openlocfilehash: c67ee699cf594f476a728c7345b47b0c32dea7ff
ms.sourcegitcommit: d2e1dfa7ef2d4e9ffae3d431cf6a4ffd9c8d378f
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 09/07/2019
ms.locfileid: "70795181"
---
# <a name="downloading-sample-databases-linq-to-dataset"></a>Téléchargement d'exemples de base de données (LINQ to DataSet)
Les exemples et les procédures pas à pas de la documentation LINQ to DataSet utilisent l’exemple de base de données AdventureWorks. Vous pouvez télécharger ce produit gratuitement à partir du site de téléchargement Microsoft. Les exemples et les procédures pas à pas de la documentation LINQ to DataSet utilisent SQL Server comme magasin de données. SQL Server Express Edition, disponible gratuitement, peut également être utilisé comme magasin de données à la place de SQL Server.  
  
## <a name="downloading-and-installing-the-adventureworks-database"></a>Téléchargement et installation de la base de données AdventureWorks  
  
#### <a name="to-download-and-install-the-adventureworks-sample-database-for-sql-server"></a>Pour télécharger et installer l'exemple de base de données AdventureWorks pour SQL Server  
  
1. Ouvrez Internet Explorer.  
  
2. Accédez au site Web des [exemples SQL Server 2005 et des exemples de bases de données](https://go.microsoft.com/fwlink/?linkid=31046) .  
  
3. Suivez les instructions pour télécharger l'exemple de base de données AdventureWorks pour votre type de processeur (AdventureWorksDB.msi par exemple), et enregistrez le fichier .MSI sur votre ordinateur local.  
  
4. Si vous disposez d'une version précédente de la base de données AdventureWorks installée à partir du téléchargement ou pendant la configuration de SQL Server, vous devez la supprimer avant d'exécuter AdventureWorks.msi.  
  
#### <a name="to-remove-a-previous-download-of-an-adventureworks-sample-database"></a>Pour supprimer un téléchargement précédent d'un exemple de base de données AdventureWorks  
  
1. Abandonnez la base de données AdventureWorks ou AdventureWorksDW.  
  
2. Dans **Ajout/suppression de programmes**, sélectionnez **AdventureWorksDB** ou **AdventureWorksBI** , puis cliquez sur **supprimer**.  
  
#### <a name="to-remove-an-adventureworks-sample-database-previously-installed-using-setup"></a>Pour supprimer un exemple de base de données AdventureWorks précédemment installé à l'aide du programme d'installation  
  
1. Abandonnez la base de données AdventureWorks ou AdventureWorksDW.  
  
2. Dans **Ajout/suppression de programmes**, sélectionnez **Microsoft SQL Server 2005** , puis cliquez sur **modifier**.  
  
3. Dans **sélection du composant**, sélectionnez composants de la **station de travail** , puis cliquez sur **suivant**.  
  
4. Dans **la page Bienvenue dans l’Assistant Installation de SQL Server**, cliquez sur **suivant**.  
  
5. Dans **vérification de la configuration système**, cliquez sur **suivant**.  
  
6. Dans **modifier ou supprimer l’instance**, cliquez sur **modifier les composants installés**.  
  
7. Dans **sélection de fonctionnalités**, développez le nœud **documentation, exemples et exemples de bases de données** .  
  
8. Sélectionnez **exemple de code et d’applications**. Développez **exemples de bases de données**, sélectionnez l’exemple de base de données à supprimer, puis sélectionnez la **fonctionnalité tout entière n’est pas disponible**. Cliquez sur **Suivant**.  
  
9. Cliquez sur **installer** , puis terminez l’Assistant installation.  
  
#### <a name="to-attach-the-adventureworks-sample-database-files-to-an-instance-of-sql-server"></a>Pour attacher les fichiers de l'exemple de base de données AdventureWorks à une instance de SQL Server  
  
1. Une fois le fichier d’installation de la base de données exemple téléchargé, double-cliquez sur le fichier **AdventureWorksDB. msi** (ou le fichier que vous avez téléchargé) pour installer la base de données. Par défaut, la base de données est installée dans c:\Program Files\Microsoft SQL Server\MSSQL.1\MSSQL\Data.  
  
2. Attachez les fichiers de la base de données AdventureWorks à une instance de SQL Server en exécutant le script suivant à l'aide de SQLCMD ou SQL Server Management Studio :  
  
    ```sql
    exec sp_attach_db @dbname=N'AdventureWorks', @filename1=N'C:\Program Files\Microsoft SQL Server\MSSQL.1\MSSQL\Data\AdventureWorks_Data.mdf', @filename2=N'C:\Program Files\Microsoft SQL Server\MSSQL.1\MSSQL\Data\AdventureWorks_log.ldf'  
    ```  
  
     Si vous avez installé ces fichiers dans un lecteur ou un répertoire différent, vous devez modifier les chemins en conséquence avant d’exécuter la procédure stockée `sp_attach_db`.  
  
## <a name="downloading-sql-server-express-edition"></a>Téléchargement de SQL Server Express Edition  
 Les exemples et les procédures pas à pas de la section LINQ to DataSet utilisent SQL Server 2005 comme magasin de données, mais ils peuvent être modifiés pour utiliser SQL Server Express Edition, à la place. SQL Server Express Edition est disponible gratuitement et vous pouvez le redistribuer avec les applications. Si vous utilisez Visual Studio, SQL Server Express édition est incluse dans les éditions professionnel et ultérieure.  
  
#### <a name="to-download-and-install-sql-server-express-edition"></a>Pour télécharger et installer SQL Server Express Edition  
  
1. Démarrez Internet Explorer.  
  
2. Accédez à la page de téléchargement [Microsoft SQL Server 2005 Express Edition](https://go.microsoft.com/fwlink/?LinkID=31070) .  
  
3. Suivez les instructions d’installation indiquées sur le site web.  
  
## <a name="see-also"></a>Voir aussi

- [Prise en main](getting-started-linq-to-dataset.md)
