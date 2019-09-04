---
title: 'Procédure : Transformer les fichiers modèle et les fichiers de mappage en ressources incorporées'
ms.date: 03/30/2017
ms.assetid: 20dfae4d-e95a-4264-9540-f5ad23b462d3
ms.openlocfilehash: c88e0c09742d76c7508d7d782eabbe46035d3501
ms.sourcegitcommit: 4e2d355baba82814fa53efd6b8bbb45bfe054d11
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 09/04/2019
ms.locfileid: "70251444"
---
# <a name="how-to-make-model-and-mapping-files-embedded-resources"></a><span data-ttu-id="92ec2-102">Procédure : Transformer les fichiers modèle et les fichiers de mappage en ressources incorporées</span><span class="sxs-lookup"><span data-stu-id="92ec2-102">How to: Make Model and Mapping Files Embedded Resources</span></span>
<span data-ttu-id="92ec2-103">Vous [!INCLUDE[adonet_ef](../../../../../includes/adonet-ef-md.md)] permet de déployer des fichiers de modèle et de mappage en tant que ressources incorporées d’une application.</span><span class="sxs-lookup"><span data-stu-id="92ec2-103">The [!INCLUDE[adonet_ef](../../../../../includes/adonet-ef-md.md)] enables you to deploy model and mapping files as embedded resources of an application.</span></span> <span data-ttu-id="92ec2-104">L'assembly comprenant les fichiers de mappage et de modèle incorporés doit être chargé dans le même domaine d'application que la connexion d'entité.</span><span class="sxs-lookup"><span data-stu-id="92ec2-104">The assembly with the embedded model and mapping files must be loaded in the same application domain as the entity connection.</span></span> <span data-ttu-id="92ec2-105">Pour plus d’informations, consultez [Chaînes de connexion](connection-strings.md).</span><span class="sxs-lookup"><span data-stu-id="92ec2-105">For more information, see [Connection Strings](connection-strings.md).</span></span> <span data-ttu-id="92ec2-106">Par défaut, les outils de Entity Data Model incorporent les fichiers de modèle et de mappage.</span><span class="sxs-lookup"><span data-stu-id="92ec2-106">By default, the Entity Data Model tools embed the model and mapping files.</span></span> <span data-ttu-id="92ec2-107">Lorsque vous définissez manuellement les fichiers de mappage et de modèle, utilisez cette procédure pour garantir que les fichiers sont déployés en tant que ressources incorporées avec une application [!INCLUDE[adonet_ef](../../../../../includes/adonet-ef-md.md)].</span><span class="sxs-lookup"><span data-stu-id="92ec2-107">When you manually define the model and mapping files, use this procedure to ensure that the files are deployed as embedded resources together with an [!INCLUDE[adonet_ef](../../../../../includes/adonet-ef-md.md)] application.</span></span>  
  
> [!NOTE]
> <span data-ttu-id="92ec2-108">Pour conserver des ressources incorporées, vous devez répéter cette procédure chaque fois que les fichiers de mappage et de modèle sont modifiés.</span><span class="sxs-lookup"><span data-stu-id="92ec2-108">To maintain embedded resources, you must repeat this procedure whenever the model and mapping files are modified.</span></span>  
  
### <a name="to-embed-model-and-mapping-files"></a><span data-ttu-id="92ec2-109">Pour incorporer les fichiers de mappage et de modèle</span><span class="sxs-lookup"><span data-stu-id="92ec2-109">To embed model and mapping files</span></span>  
  
1. <span data-ttu-id="92ec2-110">Dans **Explorateur de solutions**, sélectionnez le fichier conceptuel (. CSDL).</span><span class="sxs-lookup"><span data-stu-id="92ec2-110">In **Solution Explorer**, select the conceptual (.csdl) file.</span></span>  
  
2. <span data-ttu-id="92ec2-111">Dans le volet **Propriétés** , affectez à **action de génération** la valeur **ressource incorporée**.</span><span class="sxs-lookup"><span data-stu-id="92ec2-111">In the **Properties** pane, set **Build Action** to **Embedded Resource**.</span></span>  
  
3. <span data-ttu-id="92ec2-112">Répétez les étapes 1 et 2 pour le fichier de stockage (.ssdl) et le fichier de mappage (.msl).</span><span class="sxs-lookup"><span data-stu-id="92ec2-112">Repeat steps 1 and 2 for the storage (.ssdl) file and the mapping (.msl) file.</span></span>  
  
4. <span data-ttu-id="92ec2-113">Dans **Explorateur de solutions**, double-cliquez sur le fichier app. config, puis modifiez `Metadata` le paramètre dans `connectionString` l’attribut en fonction de l’un des formats suivants :</span><span class="sxs-lookup"><span data-stu-id="92ec2-113">In **Solution Explorer**, double-click the App.config file and then modify the `Metadata` parameter in the `connectionString` attribute based on one of the following formats:</span></span>  
  
    - <span data-ttu-id="92ec2-114">`Metadata=` `res://<assemblyFullName>/<resourceName>;`</span><span class="sxs-lookup"><span data-stu-id="92ec2-114">`Metadata=` `res://<assemblyFullName>/<resourceName>;`</span></span>  
  
    - <span data-ttu-id="92ec2-115">`Metadata=` `res://*/<resourceName>;`</span><span class="sxs-lookup"><span data-stu-id="92ec2-115">`Metadata=` `res://*/<resourceName>;`</span></span>  
  
    - `Metadata=res://*;`  
  
     <span data-ttu-id="92ec2-116">Pour plus d’informations, consultez [Chaînes de connexion](connection-strings.md).</span><span class="sxs-lookup"><span data-stu-id="92ec2-116">For more information, see [Connection Strings](connection-strings.md).</span></span>  
  
## <a name="example"></a><span data-ttu-id="92ec2-117">Exemples</span><span class="sxs-lookup"><span data-stu-id="92ec2-117">Example</span></span>  
 <span data-ttu-id="92ec2-118">La chaîne de connexion suivante référence les fichiers de mappage et de modèle incorporés pour le [modèle de vente AdventureWorks Sales Model](https://github.com/Microsoft/sql-server-samples/releases/tag/adventureworks).</span><span class="sxs-lookup"><span data-stu-id="92ec2-118">The following connection string references embedded model and mapping files for the [AdventureWorks Sales Model](https://github.com/Microsoft/sql-server-samples/releases/tag/adventureworks).</span></span> <span data-ttu-id="92ec2-119">Cette chaîne de connexion est stockée dans le fichier App.config du projet.</span><span class="sxs-lookup"><span data-stu-id="92ec2-119">This connection string is stored in the project's App.config file.</span></span>  

## <a name="see-also"></a><span data-ttu-id="92ec2-120">Voir aussi</span><span class="sxs-lookup"><span data-stu-id="92ec2-120">See also</span></span>

- [<span data-ttu-id="92ec2-121">Modélisation et mappage</span><span class="sxs-lookup"><span data-stu-id="92ec2-121">Modeling and Mapping</span></span>](modeling-and-mapping.md)
- [<span data-ttu-id="92ec2-122">Guide pratique : Définir la chaîne de connexion</span><span class="sxs-lookup"><span data-stu-id="92ec2-122">How to: Define the Connection String</span></span>](how-to-define-the-connection-string.md)
- [<span data-ttu-id="92ec2-123">Guide pratique : Créer une chaîne de connexion EntityConnection</span><span class="sxs-lookup"><span data-stu-id="92ec2-123">How to: Build an EntityConnection Connection String</span></span>](how-to-build-an-entityconnection-connection-string.md)
- <span data-ttu-id="92ec2-124">[Outils de Entity Data Model ADO.NET](https://docs.microsoft.com/previous-versions/dotnet/netframework-4.0/bb399249(v=vs.100))</span><span class="sxs-lookup"><span data-stu-id="92ec2-124">[ADO.NET Entity Data Model Tools](https://docs.microsoft.com/previous-versions/dotnet/netframework-4.0/bb399249(v=vs.100))</span></span>
