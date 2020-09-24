---
title: Création du modèle objet
ms.date: 03/30/2017
ms.assetid: 27afce86-9b1d-45fb-8e0b-636bf671a236
ms.openlocfilehash: 2191c29c0b2e56f9fdf7983bf96d2494867f318b
ms.sourcegitcommit: 5b475c1855b32cf78d2d1bbb4295e4c236f39464
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 09/24/2020
ms.locfileid: "91164361"
---
# <a name="creating-the-object-model"></a><span data-ttu-id="0d693-102">Création du modèle objet</span><span class="sxs-lookup"><span data-stu-id="0d693-102">Creating the Object Model</span></span>

<span data-ttu-id="0d693-103">Vous pouvez créer votre modèle objet à partir d'une base de données existante et l'utiliser dans son état par défaut.</span><span class="sxs-lookup"><span data-stu-id="0d693-103">You can create your object model from an existing database and use the model in its default state.</span></span> <span data-ttu-id="0d693-104">Vous pouvez également personnaliser de nombreux aspects du modèle ainsi que son comportement.</span><span class="sxs-lookup"><span data-stu-id="0d693-104">You can also customize many aspects of the model and its behavior.</span></span>  
  
 <span data-ttu-id="0d693-105">Si vous utilisez Visual Studio, vous pouvez utiliser la Concepteur Objet Relationnel pour créer votre modèle objet.</span><span class="sxs-lookup"><span data-stu-id="0d693-105">If you are using Visual Studio, you can use the Object Relational Designer to create your object model.</span></span>  
  
## <a name="in-this-section"></a><span data-ttu-id="0d693-106">Dans cette section</span><span class="sxs-lookup"><span data-stu-id="0d693-106">In This Section</span></span>  

 [<span data-ttu-id="0d693-107">Procédure : Générer le modèle objet en Visual Basic ou en C#</span><span class="sxs-lookup"><span data-stu-id="0d693-107">How to: Generate the Object Model in Visual Basic or C#</span></span>](how-to-generate-the-object-model-in-visual-basic-or-csharp.md)  
 <span data-ttu-id="0d693-108">Explique comment utiliser l'outil en ligne de commande SQLMetal.</span><span class="sxs-lookup"><span data-stu-id="0d693-108">Describes how to use the SQLMetal command-line tool.</span></span> <span data-ttu-id="0d693-109">Fournit également un lien vers le Concepteur Objet Relationnel pour les utilisateurs de Visual Studio</span><span class="sxs-lookup"><span data-stu-id="0d693-109">Also provides a link to the Object Relational Designer for Visual Studio users</span></span>  
  
 [<span data-ttu-id="0d693-110">Procédure : Générer le modèle objet sous forme de fichier externe</span><span class="sxs-lookup"><span data-stu-id="0d693-110">How to: Generate the Object Model as an External File</span></span>](how-to-generate-the-object-model-as-an-external-file.md)  
 <span data-ttu-id="0d693-111">Décrit comment générer un fichier de mappage externe au lieu d'utiliser le mappage basé sur les attributs.</span><span class="sxs-lookup"><span data-stu-id="0d693-111">Describes how to generate an external mapping file instead of using attribute-based mapping.</span></span>  
  
 [<span data-ttu-id="0d693-112">Procédure : Générer du code personnalisé en modifiant un fichier DBML</span><span class="sxs-lookup"><span data-stu-id="0d693-112">How to: Generate Customized Code by Modifying a DBML File</span></span>](how-to-generate-customized-code-by-modifying-a-dbml-file.md)  
 <span data-ttu-id="0d693-113">Décrit comment générer du code Visual Basic ou C# à partir d’un fichier de métadonnées DBML.</span><span class="sxs-lookup"><span data-stu-id="0d693-113">Describes how to generate Visual Basic or C# code from a DBML metadata file.</span></span>  
  
 [<span data-ttu-id="0d693-114">Procédure : Valider des fichiers de mappage externes et DBML</span><span class="sxs-lookup"><span data-stu-id="0d693-114">How to: Validate DBML and External Mapping Files</span></span>](how-to-validate-dbml-and-external-mapping-files.md)  
 <span data-ttu-id="0d693-115">Décrit comment valider des fichiers de mappage que vous avez modifiés (avancé).</span><span class="sxs-lookup"><span data-stu-id="0d693-115">Describes how to validate mapping files that you have modified (advanced).</span></span>  
  
 [<span data-ttu-id="0d693-116">Procédure : Rendre les entités sérialisables</span><span class="sxs-lookup"><span data-stu-id="0d693-116">How to: Make Entities Serializable</span></span>](how-to-make-entities-serializable.md)  
 <span data-ttu-id="0d693-117">Décrit comment ajouter des attributs appropriés pour rendre des entités sérialisables.</span><span class="sxs-lookup"><span data-stu-id="0d693-117">Describes how to add appropriate attributes to make entities serializable.</span></span>  
  
 [<span data-ttu-id="0d693-118">Procédure : Personnaliser des classes d’entité à l’aide de l’éditeur de code</span><span class="sxs-lookup"><span data-stu-id="0d693-118">How to: Customize Entity Classes by Using the Code Editor</span></span>](how-to-customize-entity-classes-by-using-the-code-editor.md)  
 <span data-ttu-id="0d693-119">Décrit comment utiliser l'éditeur de code pour écrire votre propre code de mappage ou personnaliser du code qui a été généré automatiquement.</span><span class="sxs-lookup"><span data-stu-id="0d693-119">Describes how to use the code editor to write your own mapping code, or customize code that has been autogenerated.</span></span>  
  
## <a name="related-sections"></a><span data-ttu-id="0d693-120">Sections connexes</span><span class="sxs-lookup"><span data-stu-id="0d693-120">Related Sections</span></span>  

 [<span data-ttu-id="0d693-121">Modèle objet LINQ to SQL</span><span class="sxs-lookup"><span data-stu-id="0d693-121">The LINQ to SQL Object Model</span></span>](the-linq-to-sql-object-model.md)  
 <span data-ttu-id="0d693-122">Fournit des détails sur le [!INCLUDE[vbtecdlinq](../../../../../../includes/vbtecdlinq-md.md)] modèle objet.</span><span class="sxs-lookup"><span data-stu-id="0d693-122">Provides details about the [!INCLUDE[vbtecdlinq](../../../../../../includes/vbtecdlinq-md.md)] object model.</span></span>  
  
 [<span data-ttu-id="0d693-123">Procédure standard d'utilisation de LINQ to SQL</span><span class="sxs-lookup"><span data-stu-id="0d693-123">Typical Steps for Using LINQ to SQL</span></span>](typical-steps-for-using-linq-to-sql.md)  
 <span data-ttu-id="0d693-124">Décrit la procédure standard à suivre pour implémenter une application [!INCLUDE[vbtecdlinq](../../../../../../includes/vbtecdlinq-md.md)].</span><span class="sxs-lookup"><span data-stu-id="0d693-124">Explains the typical steps that you follow to implement a [!INCLUDE[vbtecdlinq](../../../../../../includes/vbtecdlinq-md.md)] application.</span></span>
