---
title: Prise en charge de SqlClient pour LocalDB
ms.date: 03/30/2017
ms.assetid: cf796898-5575-46f2-ae6e-21e5aa8c4123
ms.openlocfilehash: 55ab1346de6f5c14f15d01344a984c18edf30e02
ms.sourcegitcommit: 965a5af7918acb0a3fd3baf342e15d511ef75188
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 11/18/2020
ms.locfileid: "94824478"
---
# <a name="sqlclient-support-for-localdb"></a>Prise en charge de SqlClient pour LocalDB

Cet article explique comment se connecter à une base de données de base de données locale. La base de données locale est une version allégée de SQL Server.
  
## <a name="remarks"></a>Notes
  
 Pour résumer ce que vous pouvez faire avec LocalDB :  
  
- Créez et démarrez des instances de LocalDB avec sqllocaldb.exe ou votre fichier app.config.  
  
- Utilisez sqlcmd.exe pour ajouter et modifier des bases de données dans une instance LocalDB. Par exemple : `sqlcmd -S (localdb)\myinst`.  
  
- Utilisez le mot clé de chaîne de connexion `AttachDBFilename` pour ajouter une base de données à votre instance LocalDB. Quand vous utilisez `AttachDBFilename`, si vous ne spécifiez pas le nom de la base de données avec le mot clé de chaîne de connexion `Database`, la base de données est supprimée de l’instance LocalDB quand l’application se ferme.  
  
- Spécifiez une instance LocalDB dans votre chaîne de connexion. Par exemple, si le nom de votre instance est `myInstance`, la chaîne de connexion inclut les éléments suivants :  
  
    `server=(localdb)\\myInstance`  
  
 `User Instance=True` n’est pas autorisé lors de la connexion à une base de données LocalDB.  
  
Pour plus d’informations sur l’installation de la base de données locale, consultez [SQL Server Express](/sql/database-engine/configure-windows/sql-server-express-localdb)de base.
  
## <a name="programmatically-create-a-named-instance"></a>Créer par programme une instance nommée  

 Une application peut créer une instance nommée et spécifier une base de données comme suit :  
  
- Spécifiez les instances LocalDB à créer dans le fichier app.config, comme suit.  Le numéro de version de l’instance doit être le même que le numéro de version de votre installation de LocalDB.  
  
    ```xml  
    <?xml version="1.0" encoding="utf-8" ?>  
    <configuration>  
      <configSections>  
        <section  
        name="system.data.localdb"  
        type="System.Data.LocalDBConfigurationSection,System.Data,Version=4.0.0.0,Culture=neutral,PublicKeyToken=b77a5c561934e089"/>  
      </configSections>  
      <system.data.localdb>  
        <localdbinstances>  
          <add name="myInstance" version="11.0" />  
        </localdbinstances>  
      </system.data.localdb>  
    </configuration>  
    ```  
  
- Spécifiez le nom de l’instance à l’aide du mot clé de chaîne de connexion `server`.  Le nom de l’instance spécifié dans le mot clé de chaîne de connexion `server` doit correspondre au nom spécifié dans le fichier app.config.  
  
- Utilisez le mot clé de chaîne de connexion `AttachDBFilename` pour spécifier le fichier .MDF.  
  
## <a name="see-also"></a>Voir aussi

- [Fonctionnalités de SQL Server et ADO.NET](sql-server-features-and-adonet.md)
- [Vue d'ensemble d’ADO.NET](../ado-net-overview.md)
