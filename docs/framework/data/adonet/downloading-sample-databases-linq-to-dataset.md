---
title: Téléchargement d'exemples de base de données (LINQ to DataSet)
ms.date: 03/30/2017
ms.assetid: eb42a7af-d410-4b7f-b4a8-13c72ce6fd09
ms.openlocfilehash: 340ccd1e0e2d415fe60721775bd39acf9db00f85
ms.sourcegitcommit: b1cfd260928d464d91e20121f9bdba7611c94d71
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 07/02/2019
ms.locfileid: "67504500"
---
# <a name="downloading-sample-databases-linq-to-dataset"></a>Téléchargement d'exemples de base de données (LINQ to DataSet)
Les procédures pas à pas dans le LINQ to DataSet documentation et les exemples utilisent la base de données AdventureWorks. Vous pouvez télécharger ce produit gratuitement à partir du site de téléchargement Microsoft. Les exemples et les procédures pas à pas dans le LINQ to DataSet documentation utilisent SQL Server comme magasin de données. SQL Server Express Edition, disponible gratuitement, peut également être utilisé comme magasin de données à la place de SQL Server.  
  
## <a name="downloading-and-installing-the-adventureworks-database"></a>Téléchargement et installation de la base de données AdventureWorks  
  
#### <a name="to-download-and-install-the-adventureworks-sample-database-for-sql-server"></a>Pour télécharger et installer l'exemple de base de données AdventureWorks pour SQL Server  
  
1. Ouvrez Internet Explorer.  
  
2. Accédez à la [exemples SQL Server 2005 et les bases de données exemple](https://go.microsoft.com/fwlink/?linkid=31046) site Web.  
  
3. Suivez les instructions pour télécharger l'exemple de base de données AdventureWorks pour votre type de processeur (AdventureWorksDB.msi par exemple), et enregistrez le fichier .MSI sur votre ordinateur local.  
  
4. Si vous disposez d'une version précédente de la base de données AdventureWorks installée à partir du téléchargement ou pendant la configuration de SQL Server, vous devez la supprimer avant d'exécuter AdventureWorks.msi.  
  
#### <a name="to-remove-a-previous-download-of-an-adventureworks-sample-database"></a>Pour supprimer un téléchargement précédent d'un exemple de base de données AdventureWorks  
  
1. Abandonnez la base de données AdventureWorks ou AdventureWorksDW.  
  
2. À partir de **Ajout / Suppression de programmes**, sélectionnez **AdventureWorksDB** ou **AdventureWorksBI** et cliquez sur **supprimer**.  
  
#### <a name="to-remove-an-adventureworks-sample-database-previously-installed-using-setup"></a>Pour supprimer un exemple de base de données AdventureWorks précédemment installé à l'aide du programme d'installation  
  
1. Abandonnez la base de données AdventureWorks ou AdventureWorksDW.  
  
2. À partir de **Ajout / Suppression de programmes**, sélectionnez **Microsoft SQL Server 2005** et cliquez sur **modification**.  
  
3. À partir de **sélection des composants**, sélectionnez **composants de station de travail** puis cliquez sur **suivant**.  
  
4. À partir de **Bienvenue dans l’Assistant Installation de SQL Server**, cliquez sur **suivant**.  
  
5. À partir de **System Configuration Check**, cliquez sur **suivant**.  
  
6. À partir de **changer ou supprimer l’Instance**, cliquez sur **changer les composants installés**.  
  
7. À partir de **sélection des fonctionnalités**, développez le **Documentation, exemples et exemples de bases de données** nœud.  
  
8. Sélectionnez **exemple de Code et des Applications**. Développez **Sample Databases**, sélectionnez la base de données à supprimer, puis sélectionnez **totalité de cette fonctionnalité n’est pas disponible**. Cliquez sur **Suivant**.  
  
9. Cliquez sur **installer** et terminez l’Assistant installation.  
  
#### <a name="to-attach-the-adventureworks-sample-database-files-to-an-instance-of-sql-server"></a>Pour attacher les fichiers de l'exemple de base de données AdventureWorks à une instance de SQL Server  
  
1. Une fois le fichier de programme d’installation de base de données exemple fichier téléchargé, double-cliquez sur le **AdventureWorksDB.msi** fichier (ou le fichier que vous avez téléchargé) pour installer la base de données. Par défaut, la base de données est installée dans c:\Program Files\Microsoft SQL Server\MSSQL.1\MSSQL\Data.  
  
2. Attachez les fichiers de la base de données AdventureWorks à une instance de SQL Server en exécutant le script suivant à l'aide de SQLCMD ou SQL Server Management Studio :  
  
    ```sql
    exec sp_attach_db @dbname=N'AdventureWorks', @filename1=N'C:\Program Files\Microsoft SQL Server\MSSQL.1\MSSQL\Data\AdventureWorks_Data.mdf', @filename2=N'C:\Program Files\Microsoft SQL Server\MSSQL.1\MSSQL\Data\AdventureWorks_log.ldf'  
    ```  
  
     Si vous avez installé ces fichiers dans un lecteur ou un répertoire différent, vous devez modifier les chemins en conséquence avant d’exécuter la procédure stockée `sp_attach_db`.  
  
## <a name="downloading-sql-server-express-edition"></a>Téléchargement de SQL Server Express Edition  
 Les exemples et les procédures pas à pas dans le LINQ to DataSet section utiliser SQL Server 2005 comme magasin de données, mais peut être modifié pour utiliser SQL Server Express Edition, à la place. SQL Server Express Edition est disponible gratuitement et vous pouvez le redistribuer avec les applications. Si vous utilisez Visual Studio, SQL Server Express Edition est incluse dans les éditions professionnelles et ultérieures.  
  
#### <a name="to-download-and-install-sql-server-express-edition"></a>Pour télécharger et installer SQL Server Express Edition  
  
1. Démarrez Internet Explorer.  
  
2. Accédez à la [Microsoft SQL Server 2005 Express Edition](https://go.microsoft.com/fwlink/?LinkID=31070) page de téléchargement.  
  
3. Suivez les instructions d’installation indiquées sur le site web.  
  
## <a name="see-also"></a>Voir aussi

- [Prise en main](../../../../docs/framework/data/adonet/getting-started-linq-to-dataset.md)
