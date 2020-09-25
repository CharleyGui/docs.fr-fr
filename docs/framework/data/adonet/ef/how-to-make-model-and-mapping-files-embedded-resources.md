---
title: 'Procédure : Transformer les fichiers modèle et les fichiers de mappage en ressources incorporées'
ms.date: 03/30/2017
ms.assetid: 20dfae4d-e95a-4264-9540-f5ad23b462d3
ms.openlocfilehash: 8496dcad5422d1a45af52e58325efd360768da34
ms.sourcegitcommit: 5b475c1855b32cf78d2d1bbb4295e4c236f39464
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 09/24/2020
ms.locfileid: "91198286"
---
# <a name="how-to-make-model-and-mapping-files-embedded-resources"></a><span data-ttu-id="2bcf3-102">Procédure : Transformer les fichiers modèle et les fichiers de mappage en ressources incorporées</span><span class="sxs-lookup"><span data-stu-id="2bcf3-102">How to: Make Model and Mapping Files Embedded Resources</span></span>

<span data-ttu-id="2bcf3-103">Le Entity Framework vous permet de déployer des fichiers de modèle et de mappage en tant que ressources incorporées d’une application.</span><span class="sxs-lookup"><span data-stu-id="2bcf3-103">The Entity Framework enables you to deploy model and mapping files as embedded resources of an application.</span></span> <span data-ttu-id="2bcf3-104">L'assembly comprenant les fichiers de mappage et de modèle incorporés doit être chargé dans le même domaine d'application que la connexion d'entité.</span><span class="sxs-lookup"><span data-stu-id="2bcf3-104">The assembly with the embedded model and mapping files must be loaded in the same application domain as the entity connection.</span></span> <span data-ttu-id="2bcf3-105">Pour plus d’informations, consultez [chaînes de connexion](connection-strings.md).</span><span class="sxs-lookup"><span data-stu-id="2bcf3-105">For more information, see [Connection Strings](connection-strings.md).</span></span> <span data-ttu-id="2bcf3-106">Par défaut, les outils de Entity Data Model incorporent les fichiers de modèle et de mappage.</span><span class="sxs-lookup"><span data-stu-id="2bcf3-106">By default, the Entity Data Model tools embed the model and mapping files.</span></span> <span data-ttu-id="2bcf3-107">Lorsque vous définissez manuellement les fichiers de modèle et de mappage, utilisez cette procédure pour vous assurer que les fichiers sont déployés en tant que ressources incorporées avec une application Entity Framework.</span><span class="sxs-lookup"><span data-stu-id="2bcf3-107">When you manually define the model and mapping files, use this procedure to ensure that the files are deployed as embedded resources together with an Entity Framework application.</span></span>  
  
> [!NOTE]
> <span data-ttu-id="2bcf3-108">Pour conserver des ressources incorporées, vous devez répéter cette procédure chaque fois que les fichiers de mappage et de modèle sont modifiés.</span><span class="sxs-lookup"><span data-stu-id="2bcf3-108">To maintain embedded resources, you must repeat this procedure whenever the model and mapping files are modified.</span></span>  
  
### <a name="to-embed-model-and-mapping-files"></a><span data-ttu-id="2bcf3-109">Pour incorporer les fichiers de mappage et de modèle</span><span class="sxs-lookup"><span data-stu-id="2bcf3-109">To embed model and mapping files</span></span>  
  
1. <span data-ttu-id="2bcf3-110">Dans **Explorateur de solutions**, sélectionnez le fichier conceptuel (. CSDL).</span><span class="sxs-lookup"><span data-stu-id="2bcf3-110">In **Solution Explorer**, select the conceptual (.csdl) file.</span></span>  
  
2. <span data-ttu-id="2bcf3-111">Dans le volet **Propriétés** , affectez à **action de génération** la valeur **ressource incorporée**.</span><span class="sxs-lookup"><span data-stu-id="2bcf3-111">In the **Properties** pane, set **Build Action** to **Embedded Resource**.</span></span>  
  
3. <span data-ttu-id="2bcf3-112">Répétez les étapes 1 et 2 pour le fichier de stockage (.ssdl) et le fichier de mappage (.msl).</span><span class="sxs-lookup"><span data-stu-id="2bcf3-112">Repeat steps 1 and 2 for the storage (.ssdl) file and the mapping (.msl) file.</span></span>  
  
4. <span data-ttu-id="2bcf3-113">Dans **Explorateur de solutions**, double-cliquez sur le fichier App.config, puis modifiez le `Metadata` paramètre dans l' `connectionString` attribut en fonction de l’un des formats suivants :</span><span class="sxs-lookup"><span data-stu-id="2bcf3-113">In **Solution Explorer**, double-click the App.config file and then modify the `Metadata` parameter in the `connectionString` attribute based on one of the following formats:</span></span>  
  
    - <span data-ttu-id="2bcf3-114">`Metadata=` `res://<assemblyFullName>/<resourceName>;`</span><span class="sxs-lookup"><span data-stu-id="2bcf3-114">`Metadata=` `res://<assemblyFullName>/<resourceName>;`</span></span>  
  
    - <span data-ttu-id="2bcf3-115">`Metadata=` `res://*/<resourceName>;`</span><span class="sxs-lookup"><span data-stu-id="2bcf3-115">`Metadata=` `res://*/<resourceName>;`</span></span>  
  
    - `Metadata=res://*;`  
  
     <span data-ttu-id="2bcf3-116">Pour plus d’informations, consultez [chaînes de connexion](connection-strings.md).</span><span class="sxs-lookup"><span data-stu-id="2bcf3-116">For more information, see [Connection Strings](connection-strings.md).</span></span>  
  
## <a name="example"></a><span data-ttu-id="2bcf3-117">Exemple</span><span class="sxs-lookup"><span data-stu-id="2bcf3-117">Example</span></span>  

 <span data-ttu-id="2bcf3-118">La chaîne de connexion suivante référence les fichiers de mappage et de modèle incorporés pour le [modèle de vente AdventureWorks Sales Model](https://github.com/Microsoft/sql-server-samples/releases/tag/adventureworks).</span><span class="sxs-lookup"><span data-stu-id="2bcf3-118">The following connection string references embedded model and mapping files for the [AdventureWorks Sales Model](https://github.com/Microsoft/sql-server-samples/releases/tag/adventureworks).</span></span> <span data-ttu-id="2bcf3-119">Cette chaîne de connexion est stockée dans le fichier App.config du projet.</span><span class="sxs-lookup"><span data-stu-id="2bcf3-119">This connection string is stored in the project's App.config file.</span></span>  

## <a name="see-also"></a><span data-ttu-id="2bcf3-120">Voir aussi</span><span class="sxs-lookup"><span data-stu-id="2bcf3-120">See also</span></span>

- [<span data-ttu-id="2bcf3-121">Modélisation et mappage</span><span class="sxs-lookup"><span data-stu-id="2bcf3-121">Modeling and Mapping</span></span>](modeling-and-mapping.md)
- [<span data-ttu-id="2bcf3-122">Procédure : Définir la chaîne de connexion</span><span class="sxs-lookup"><span data-stu-id="2bcf3-122">How to: Define the Connection String</span></span>](how-to-define-the-connection-string.md)
- [<span data-ttu-id="2bcf3-123">Procédure : Créer une chaîne de connexion EntityConnection</span><span class="sxs-lookup"><span data-stu-id="2bcf3-123">How to: Build an EntityConnection Connection String</span></span>](how-to-build-an-entityconnection-connection-string.md)
- <span data-ttu-id="2bcf3-124">[Outils de Entity Data Model ADO.NET](/previous-versions/dotnet/netframework-4.0/bb399249(v=vs.100))</span><span class="sxs-lookup"><span data-stu-id="2bcf3-124">[ADO.NET Entity Data Model Tools](/previous-versions/dotnet/netframework-4.0/bb399249(v=vs.100))</span></span>
