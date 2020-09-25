---
title: Prise en charge de SqlClient pour LocalDB
ms.date: 03/30/2017
ms.assetid: cf796898-5575-46f2-ae6e-21e5aa8c4123
ms.openlocfilehash: 841c455605b0b32668d26cab16a6207dc1c0f716
ms.sourcegitcommit: 5b475c1855b32cf78d2d1bbb4295e4c236f39464
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 09/24/2020
ms.locfileid: "91203421"
---
# <a name="sqlclient-support-for-localdb"></a><span data-ttu-id="9d46d-102">Prise en charge de SqlClient pour LocalDB</span><span class="sxs-lookup"><span data-stu-id="9d46d-102">SqlClient Support for LocalDB</span></span>

<span data-ttu-id="9d46d-103">À compter du nom de code SQL Server Denali, une version légère de SQL Server, appelée LocalDB, sera disponible.</span><span class="sxs-lookup"><span data-stu-id="9d46d-103">Beginning in SQL Server code name Denali, a lightweight version of SQL Server, called LocalDB, will be available.</span></span> <span data-ttu-id="9d46d-104">Cette rubrique explique comment se connecter à une base de données LocalDB.</span><span class="sxs-lookup"><span data-stu-id="9d46d-104">This topic discusses how to connect to a LocalDB database.</span></span>  
  
## <a name="remarks"></a><span data-ttu-id="9d46d-105">Notes</span><span class="sxs-lookup"><span data-stu-id="9d46d-105">Remarks</span></span>  

 <span data-ttu-id="9d46d-106">Pour plus d’informations sur LocalDB, notamment comment installer LocalDB et configurer votre instance LocalDB, consultez la Documentation en ligne de SQL Server.</span><span class="sxs-lookup"><span data-stu-id="9d46d-106">For more information about LocalDB, including how to install LocalDB and configure your LocalDB instance, see SQL Server Books Online.</span></span>  
  
 <span data-ttu-id="9d46d-107">Pour résumer ce que vous pouvez faire avec LocalDB :</span><span class="sxs-lookup"><span data-stu-id="9d46d-107">To summarize what you can do with LocalDB:</span></span>  
  
- <span data-ttu-id="9d46d-108">Créez et démarrez des instances de LocalDB avec sqllocaldb.exe ou votre fichier app.config.</span><span class="sxs-lookup"><span data-stu-id="9d46d-108">Create and start LocalDB instances with sqllocaldb.exe or your app.config file.</span></span>  
  
- <span data-ttu-id="9d46d-109">Utilisez sqlcmd.exe pour ajouter et modifier des bases de données dans une instance LocalDB.</span><span class="sxs-lookup"><span data-stu-id="9d46d-109">Use sqlcmd.exe to add and modify databases in a LocalDB instance.</span></span> <span data-ttu-id="9d46d-110">Par exemple : `sqlcmd -S (localdb)\myinst`.</span><span class="sxs-lookup"><span data-stu-id="9d46d-110">For example, `sqlcmd -S (localdb)\myinst`.</span></span>  
  
- <span data-ttu-id="9d46d-111">Utilisez le mot clé de chaîne de connexion `AttachDBFilename` pour ajouter une base de données à votre instance LocalDB.</span><span class="sxs-lookup"><span data-stu-id="9d46d-111">Use the `AttachDBFilename` connection string keyword to add a database to your LocalDB instance.</span></span> <span data-ttu-id="9d46d-112">Quand vous utilisez `AttachDBFilename`, si vous ne spécifiez pas le nom de la base de données avec le mot clé de chaîne de connexion `Database`, la base de données est supprimée de l’instance LocalDB quand l’application se ferme.</span><span class="sxs-lookup"><span data-stu-id="9d46d-112">When using `AttachDBFilename`, if you do not specify the name of the database with the `Database` connection string keyword, the database will be removed from the LocalDB instance when the application closes.</span></span>  
  
- <span data-ttu-id="9d46d-113">Spécifiez une instance LocalDB dans votre chaîne de connexion.</span><span class="sxs-lookup"><span data-stu-id="9d46d-113">Specify a LocalDB instance in your connection string.</span></span> <span data-ttu-id="9d46d-114">Par exemple, si le nom de votre instance est `myInstance`, la chaîne de connexion inclut les éléments suivants :</span><span class="sxs-lookup"><span data-stu-id="9d46d-114">For example, your instance name is `myInstance`, the connection string would include:</span></span>  
  
    `server=(localdb)\\myInstance`  
  
 <span data-ttu-id="9d46d-115">`User Instance=True` n’est pas autorisé lors de la connexion à une base de données LocalDB.</span><span class="sxs-lookup"><span data-stu-id="9d46d-115">`User Instance=True` is not allowed when connecting to a LocalDB database.</span></span>  
  
 <span data-ttu-id="9d46d-116">Vous pouvez télécharger LocalDB à partir de [Microsoft SQL Server 2012 Feature Pack](https://www.microsoft.com/download/en/details.aspx?id=29065).</span><span class="sxs-lookup"><span data-stu-id="9d46d-116">You can download LocalDB from [Microsoft SQL Server 2012 Feature Pack](https://www.microsoft.com/download/en/details.aspx?id=29065).</span></span> <span data-ttu-id="9d46d-117">Si vous devez utiliser sqlcmd.exe pour modifier des données dans votre instance de LocalDB, vous aurez besoin du sqlcmd de SQL Server 2012, que vous pouvez également obtenir dans SQL Server 2012 Feature Pack.</span><span class="sxs-lookup"><span data-stu-id="9d46d-117">If you will use sqlcmd.exe to modify data in your LocalDB instance, you will need sqlcmd from SQL Server 2012, which you can also get from the SQL Server 2012 Feature Pack.</span></span>  
  
## <a name="programmatically-create-a-named-instance"></a><span data-ttu-id="9d46d-118">Créer par programme une instance nommée</span><span class="sxs-lookup"><span data-stu-id="9d46d-118">Programmatically Create a Named Instance</span></span>  

 <span data-ttu-id="9d46d-119">Une application peut créer une instance nommée et spécifier une base de données comme suit :</span><span class="sxs-lookup"><span data-stu-id="9d46d-119">An application can create a named instance and specify a database as follows:</span></span>  
  
- <span data-ttu-id="9d46d-120">Spécifiez les instances LocalDB à créer dans le fichier app.config, comme suit.</span><span class="sxs-lookup"><span data-stu-id="9d46d-120">Specify the LocalDB instances to create in the app.config file, as follows.</span></span>  <span data-ttu-id="9d46d-121">Le numéro de version de l’instance doit être le même que le numéro de version de votre installation de LocalDB.</span><span class="sxs-lookup"><span data-stu-id="9d46d-121">The version number of the instance should be the same as the version number of your LocalDB installation.</span></span>  
  
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
  
- <span data-ttu-id="9d46d-122">Spécifiez le nom de l’instance à l’aide du mot clé de chaîne de connexion `server`.</span><span class="sxs-lookup"><span data-stu-id="9d46d-122">Specify the name of the instance using the `server` connection string keyword.</span></span>  <span data-ttu-id="9d46d-123">Le nom de l’instance spécifié dans le mot clé de chaîne de connexion `server` doit correspondre au nom spécifié dans le fichier app.config.</span><span class="sxs-lookup"><span data-stu-id="9d46d-123">The instance name specified in the `server` connection string keyword must match the name specified in the app.config file.</span></span>  
  
- <span data-ttu-id="9d46d-124">Utilisez le mot clé de chaîne de connexion `AttachDBFilename` pour spécifier le fichier .MDF.</span><span class="sxs-lookup"><span data-stu-id="9d46d-124">Use the `AttachDBFilename` connection string keyword to specify the .MDF file.</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="9d46d-125">Voir aussi</span><span class="sxs-lookup"><span data-stu-id="9d46d-125">See also</span></span>

- [<span data-ttu-id="9d46d-126">Fonctionnalités de SQL Server et ADO.NET</span><span class="sxs-lookup"><span data-stu-id="9d46d-126">SQL Server Features and ADO.NET</span></span>](sql-server-features-and-adonet.md)
- [<span data-ttu-id="9d46d-127">Vue d'ensemble d’ADO.NET</span><span class="sxs-lookup"><span data-stu-id="9d46d-127">ADO.NET Overview</span></span>](../ado-net-overview.md)
