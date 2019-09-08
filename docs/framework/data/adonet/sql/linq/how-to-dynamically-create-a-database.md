---
title: 'Procédure : Créer dynamiquement une base de données'
ms.date: 03/30/2017
dev_langs:
- csharp
- vb
ms.assetid: fb7f23c4-4572-4c38-9898-a287807d070c
ms.openlocfilehash: 4cadf20cdadb39483f26a29619cae058eac47e50
ms.sourcegitcommit: d2e1dfa7ef2d4e9ffae3d431cf6a4ffd9c8d378f
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 09/07/2019
ms.locfileid: "70793659"
---
# <a name="how-to-dynamically-create-a-database"></a><span data-ttu-id="44588-102">Procédure : Créer dynamiquement une base de données</span><span class="sxs-lookup"><span data-stu-id="44588-102">How to: Dynamically Create a Database</span></span>
<span data-ttu-id="44588-103">Dans LINQ to SQL, un modèle objet est mappé à une base de données relationnelle.</span><span class="sxs-lookup"><span data-stu-id="44588-103">In LINQ to SQL, an object model is mapped to a relational database.</span></span> <span data-ttu-id="44588-104">Le mappage est activé à l'aide du mappage basé sur les attributs ou d'un fichier de mappage externe pour décrire la structure de la base de données relationnelle.</span><span class="sxs-lookup"><span data-stu-id="44588-104">Mapping is enabled by using attribute-based mapping or an external mapping file to describe the structure of the relational database.</span></span> <span data-ttu-id="44588-105">Dans les deux scénarios, il existe suffisamment d'informations sur la base de données relationnelle pour pouvoir créer une nouvelle instance de la base de données à l'aide de la méthode <xref:System.Data.Linq.DataContext.CreateDatabase%2A?displayProperty=nameWithType>.</span><span class="sxs-lookup"><span data-stu-id="44588-105">In both scenarios, there is enough information about the relational database that you can create a new instance of the database using the <xref:System.Data.Linq.DataContext.CreateDatabase%2A?displayProperty=nameWithType> method.</span></span>  
  
 <span data-ttu-id="44588-106">La méthode <xref:System.Data.Linq.DataContext.CreateDatabase%2A?displayProperty=nameWithType> crée un réplica de la base de données uniquement en fonction de l'étendue des informations encodées dans le modèle objet.</span><span class="sxs-lookup"><span data-stu-id="44588-106">The <xref:System.Data.Linq.DataContext.CreateDatabase%2A?displayProperty=nameWithType> method creates a replica of the database only to the extent of the information encoded in the object model.</span></span> <span data-ttu-id="44588-107">Les fichiers et les attributs de mappage de votre modèle objet ne peuvent pas encoder l'ensemble des éléments de la structure d'une base de données existante.</span><span class="sxs-lookup"><span data-stu-id="44588-107">Mapping files and attributes from your object model might not encode everything about the structure of an existing database.</span></span> <span data-ttu-id="44588-108">Les informations de mappage ne représentent pas le contenu de fonctions définies par l'utilisateur, de procédures stockées, de déclencheurs ou de contraintes de validation.</span><span class="sxs-lookup"><span data-stu-id="44588-108">Mapping information does not represent the contents of user-defined functions, stored procedures, triggers, or check constraints.</span></span> <span data-ttu-id="44588-109">Ce comportement est suffisant pour différentes bases de données.</span><span class="sxs-lookup"><span data-stu-id="44588-109">This behavior is sufficient for a variety of databases.</span></span>  
  
 <span data-ttu-id="44588-110">Vous pouvez utiliser la méthode <xref:System.Data.Linq.DataContext.CreateDatabase%2A?displayProperty=nameWithType> dans le nombre de scénarios souhaité, surtout si un fournisseur de données connu tel que Microsoft SQL Server 2008 est disponible.</span><span class="sxs-lookup"><span data-stu-id="44588-110">You can use the <xref:System.Data.Linq.DataContext.CreateDatabase%2A?displayProperty=nameWithType> method in any number of scenarios, especially if a known data provider like Microsoft SQL Server 2008 is available.</span></span> <span data-ttu-id="44588-111">Dans les scénarios classiques :</span><span class="sxs-lookup"><span data-stu-id="44588-111">Typical scenarios include the following:</span></span>  
  
- <span data-ttu-id="44588-112">Vous générez une application qui s'installe automatiquement sur le système d'un client.</span><span class="sxs-lookup"><span data-stu-id="44588-112">You are building an application that automatically installs itself on a customer system.</span></span>  
  
- <span data-ttu-id="44588-113">Vous générez une application cliente qui a besoin d'une base de données locale pour enregistrer son état hors connexion.</span><span class="sxs-lookup"><span data-stu-id="44588-113">You are building a client application that needs a local database to save its offline state.</span></span>  
  
 <span data-ttu-id="44588-114">Vous pouvez également utiliser la méthode <xref:System.Data.Linq.DataContext.CreateDatabase%2A?displayProperty=nameWithType> avec SQL Server en utilisant un fichier .mdf ou un nom de catalogue, en fonction de votre chaîne de connexion.</span><span class="sxs-lookup"><span data-stu-id="44588-114">You can also use the <xref:System.Data.Linq.DataContext.CreateDatabase%2A?displayProperty=nameWithType> method with SQL Server by using an .mdf file or a catalog name, depending on your connection string.</span></span> [!INCLUDE[vbtecdlinq](../../../../../../includes/vbtecdlinq-md.md)] <span data-ttu-id="44588-115">utilise la chaîne de connexion pour définir la base de données à créer et sur quel serveur la base de données sera créée.</span><span class="sxs-lookup"><span data-stu-id="44588-115">uses the connection string to define the database to be created and on which server the database is to be created.</span></span>  
  
> [!NOTE]
> <span data-ttu-id="44588-116">Si possible, utilisez la sécurité intégrée Windows pour vous connecter à la base de données de façon à ce que les mots de passe ne soient pas requis dans la chaîne de connexion.</span><span class="sxs-lookup"><span data-stu-id="44588-116">Whenever possible, use Windows Integrated Security to connect to the database so that passwords are not required in the connection string.</span></span>  
  
## <a name="example"></a><span data-ttu-id="44588-117">Exemple</span><span class="sxs-lookup"><span data-stu-id="44588-117">Example</span></span>  
 <span data-ttu-id="44588-118">Le code suivant fournit un exemple de création d'une nouvelle base de données nommée MyDVDs.mdf.</span><span class="sxs-lookup"><span data-stu-id="44588-118">The following code provides an example of how to create a new database named MyDVDs.mdf.</span></span>  
  
 [!code-csharp[DLinqSubmittingChanges#5](../../../../../../samples/snippets/csharp/VS_Snippets_Data/DLinqSubmittingChanges/cs/Program.cs#5)]
 [!code-vb[DLinqSubmittingChanges#5](../../../../../../samples/snippets/visualbasic/VS_Snippets_Data/DLinqSubmittingChanges/vb/Module1.vb#5)]  
  
## <a name="example"></a><span data-ttu-id="44588-119">Exemples</span><span class="sxs-lookup"><span data-stu-id="44588-119">Example</span></span>  
 <span data-ttu-id="44588-120">Vous pouvez utiliser le modèle objet pour créer une base de données en procédant comme suit :</span><span class="sxs-lookup"><span data-stu-id="44588-120">You can use the object model to create a database by doing the following:</span></span>  
  
 [!code-csharp[DLinqSubmittingChanges#6](../../../../../../samples/snippets/csharp/VS_Snippets_Data/DLinqSubmittingChanges/cs/Program.cs#6)]
 [!code-vb[DLinqSubmittingChanges#6](../../../../../../samples/snippets/visualbasic/VS_Snippets_Data/DLinqSubmittingChanges/vb/Module1.vb#6)]  
  
## <a name="example"></a><span data-ttu-id="44588-121">Exemples</span><span class="sxs-lookup"><span data-stu-id="44588-121">Example</span></span>  
 <span data-ttu-id="44588-122">Lors de la création d’une application qui s’installe automatiquement sur le système d’un client, vérifiez si la base de données existe déjà et supprimez-la avant d’un créer une nouvelle.</span><span class="sxs-lookup"><span data-stu-id="44588-122">When building an application that automatically installs itself on a  customer system, see if the database already exists and drop it before creating a new one.</span></span> <span data-ttu-id="44588-123">La classe <xref:System.Data.Linq.DataContext> fournit les méthodes <xref:System.Data.Linq.DataContext.DatabaseExists%2A> et <xref:System.Data.Linq.DataContext.DeleteDatabase%2A> pour vous aider dans cette tâche.</span><span class="sxs-lookup"><span data-stu-id="44588-123">The <xref:System.Data.Linq.DataContext> class provides the <xref:System.Data.Linq.DataContext.DatabaseExists%2A> and <xref:System.Data.Linq.DataContext.DeleteDatabase%2A> methods to help you with this process.</span></span>  
  
 <span data-ttu-id="44588-124">L'exemple suivant illustre une utilisation de ces méthodes pour implémenter cette approche :</span><span class="sxs-lookup"><span data-stu-id="44588-124">The following example shows one way these methods can be used to implement this approach:</span></span>  
  
 [!code-csharp[DLinqSubmittingChanges#7](../../../../../../samples/snippets/csharp/VS_Snippets_Data/DLinqSubmittingChanges/cs/Program.cs#7)]
 [!code-vb[DLinqSubmittingChanges#7](../../../../../../samples/snippets/visualbasic/VS_Snippets_Data/DLinqSubmittingChanges/vb/Module1.vb#7)]  
  
## <a name="see-also"></a><span data-ttu-id="44588-125">Voir aussi</span><span class="sxs-lookup"><span data-stu-id="44588-125">See also</span></span>

- [<span data-ttu-id="44588-126">Mappage basé sur les attributs</span><span class="sxs-lookup"><span data-stu-id="44588-126">Attribute-Based Mapping</span></span>](attribute-based-mapping.md)
- [<span data-ttu-id="44588-127">Mappage externe</span><span class="sxs-lookup"><span data-stu-id="44588-127">External Mapping</span></span>](external-mapping.md)
- [<span data-ttu-id="44588-128">Mappage de type SQL-CLR</span><span class="sxs-lookup"><span data-stu-id="44588-128">SQL-CLR Type Mapping</span></span>](sql-clr-type-mapping.md)
- [<span data-ttu-id="44588-129">Informations générales</span><span class="sxs-lookup"><span data-stu-id="44588-129">Background Information</span></span>](background-information.md)
- [<span data-ttu-id="44588-130">Apport et soumission de modifications de données</span><span class="sxs-lookup"><span data-stu-id="44588-130">Making and Submitting Data Changes</span></span>](making-and-submitting-data-changes.md)
