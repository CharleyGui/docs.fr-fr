---
title: Utilisation du langage de définition de données
ms.date: 03/30/2017
dev_langs:
- csharp
- vb
ms.assetid: ec50083d-44f4-4093-9b23-5eacd601f96e
ms.openlocfilehash: c30cbbc1eae6d4cbcadb9bfe8d267fb428764971
ms.sourcegitcommit: 5b475c1855b32cf78d2d1bbb4295e4c236f39464
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 09/24/2020
ms.locfileid: "91200886"
---
# <a name="working-with-data-definition-language"></a><span data-ttu-id="9db36-102">Utilisation du langage de définition de données</span><span class="sxs-lookup"><span data-stu-id="9db36-102">Working with Data Definition Language</span></span>

<span data-ttu-id="9db36-103">À partir du .NET Framework version 4, le Entity Framework prend en charge le langage de définition de données (DDL).</span><span class="sxs-lookup"><span data-stu-id="9db36-103">Starting with the .NET Framework version 4, the Entity Framework supports data definition language (DDL).</span></span> <span data-ttu-id="9db36-104">Cela vous permet de créer ou de supprimer une instance de base de données selon la chaîne de connexion et les métadonnées du modèle de stockage (SSDL).</span><span class="sxs-lookup"><span data-stu-id="9db36-104">This allows you to create or delete a database instance based on the connection string and the metadata of the storage (SSDL) model.</span></span>  
  
 <span data-ttu-id="9db36-105">Les méthodes suivantes sur l'objet <xref:System.Data.Objects.ObjectContext> utilisent la chaîne de connexion et le contenu SSDL pour effectuer les opérations suivantes : créer ou supprimer la base de données, vérifier si la base de données existe et consulter le script DDL généré :</span><span class="sxs-lookup"><span data-stu-id="9db36-105">The following methods on the <xref:System.Data.Objects.ObjectContext> use the connection string and the SSDL content to accomplish the following: create or delete the database, check whether the database exists, and view the generated DDL script:</span></span>  
  
- <xref:System.Data.Objects.ObjectContext.CreateDatabase%2A>  
  
- <xref:System.Data.Objects.ObjectContext.DeleteDatabase%2A>  
  
- <xref:System.Data.Objects.ObjectContext.DatabaseExists%2A>  
  
- <xref:System.Data.Objects.ObjectContext.CreateDatabaseScript%2A>  
  
> [!NOTE]
> <span data-ttu-id="9db36-106">L'exécution des commandes DDL exige de disposer d'autorisations suffisantes.</span><span class="sxs-lookup"><span data-stu-id="9db36-106">Executing the DDL commands assumes sufficient permissions.</span></span>  
  
 <span data-ttu-id="9db36-107">Les méthodes précédemment répertoriées délèguent la plupart du travail au fournisseur de données ADO.NET sous-jacent.</span><span class="sxs-lookup"><span data-stu-id="9db36-107">The methods previously listed delegate most of the work to the underlying ADO.NET data provider.</span></span> <span data-ttu-id="9db36-108">Il incombe au fournisseur de vérifier que la convention d'affectation des noms utilisée pour générer les objets de base de données correspond aux conventions utilisées pour l'interrogation et les mises à jour.</span><span class="sxs-lookup"><span data-stu-id="9db36-108">It is the provider’s responsibility to ensure that the naming convention used to generate database objects is consistent with conventions used for querying and updates.</span></span>  
  
 <span data-ttu-id="9db36-109">L'exemple suivant vous indique comment générer la base de données selon le modèle existant.</span><span class="sxs-lookup"><span data-stu-id="9db36-109">The following example shows you how to generate the database based on the existing model.</span></span> <span data-ttu-id="9db36-110">Il ajoute également un nouvel objet entité au contexte de l'objet puis l'enregistre dans la base de données.</span><span class="sxs-lookup"><span data-stu-id="9db36-110">It also adds a new entity object to the object context and then saves it to the database.</span></span>  
  
## <a name="procedures"></a><span data-ttu-id="9db36-111">Procédures</span><span class="sxs-lookup"><span data-stu-id="9db36-111">Procedures</span></span>  
  
### <a name="to-define-a-database-based-on-the-existing-model"></a><span data-ttu-id="9db36-112">Pour définir une base de données selon le modèle existant</span><span class="sxs-lookup"><span data-stu-id="9db36-112">To define a database based on the existing model</span></span>  
  
1. <span data-ttu-id="9db36-113">Créez une application console.</span><span class="sxs-lookup"><span data-stu-id="9db36-113">Create a console application.</span></span>  
  
2. <span data-ttu-id="9db36-114">Ajoutez un modèle existant à votre application.</span><span class="sxs-lookup"><span data-stu-id="9db36-114">Add an existing model to your application.</span></span>  
  
    1. <span data-ttu-id="9db36-115">Ajoutez un modèle vide nommé `SchoolModel` .</span><span class="sxs-lookup"><span data-stu-id="9db36-115">Add an empty model named `SchoolModel`.</span></span> <span data-ttu-id="9db36-116">Pour créer un modèle vide, consultez la rubrique [How to : Create a New. edmx file](/previous-versions/dotnet/netframework-4.0/cc716703(v=vs.100)) .</span><span class="sxs-lookup"><span data-stu-id="9db36-116">To create an empty model, see the [How to: Create a New .edmx File](/previous-versions/dotnet/netframework-4.0/cc716703(v=vs.100)) topic.</span></span>  
  
     <span data-ttu-id="9db36-117">Le fichier SchoolModel.edmx est ajouté à votre projet.</span><span class="sxs-lookup"><span data-stu-id="9db36-117">The SchoolModel.edmx file is added to your project.</span></span>  
  
    1. <span data-ttu-id="9db36-118">Copiez le contenu conceptuel, de stockage et de mappage pour le modèle School à partir de la rubrique [modèle School](/previous-versions/dotnet/netframework-4.0/bb896300(v=vs.100)) .</span><span class="sxs-lookup"><span data-stu-id="9db36-118">Copy the conceptual, storage, and mapping content for the School model from the [School Model](/previous-versions/dotnet/netframework-4.0/bb896300(v=vs.100)) topic.</span></span>  
  
    2. <span data-ttu-id="9db36-119">Ouvrez le fichier SchoolModel.edmx et collez le contenu dans les balises `edmx:Runtime`.</span><span class="sxs-lookup"><span data-stu-id="9db36-119">Open the SchoolModel.edmx file and paste the content within the `edmx:Runtime` tags.</span></span>  
  
3. <span data-ttu-id="9db36-120">Ajoutez le code suivant à votre fonction principale.</span><span class="sxs-lookup"><span data-stu-id="9db36-120">Add the following code to your main function.</span></span> <span data-ttu-id="9db36-121">Le code initialise la chaîne de connexion à votre serveur de base de données, consulte le script DDL, crée la base de données, ajoute une nouvelle entité au contexte et enregistre les modifications dans la base de données.</span><span class="sxs-lookup"><span data-stu-id="9db36-121">The code initializes the connection string to your database server, views the DDL script, creates the database, adds a new entity to the context, and saves the changes to the database.</span></span>  
  
     [!code-csharp[DP ObjectServices Concepts#DDL](../../../../../samples/snippets/csharp/VS_Snippets_Data/DP ObjectServices Concepts/CS/Source.cs#ddl)]
     [!code-vb[DP ObjectServices Concepts#DDL](../../../../../samples/snippets/visualbasic/VS_Snippets_Data/DP ObjectServices Concepts/VB/Source.vb#ddl)]
