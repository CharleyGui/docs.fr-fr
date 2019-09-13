---
title: Créer un projet LINQ to DataSet dans Visual Studio
ms.date: 08/15/2018
ms.assetid: 49ba6cb0-cdd2-4571-aeaa-25bf0f40e9b3
ms.openlocfilehash: 8b905c65575c3c567459d843b2a5d1606bc63228
ms.sourcegitcommit: d2e1dfa7ef2d4e9ffae3d431cf6a4ffd9c8d378f
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 09/07/2019
ms.locfileid: "70783778"
---
# <a name="how-to-create-a-linq-to-dataset-project-in-visual-studio"></a><span data-ttu-id="7f288-102">Procédure : Créer un projet LINQ to DataSet dans Visual Studio</span><span class="sxs-lookup"><span data-stu-id="7f288-102">How to: Create a LINQ to DataSet project In Visual Studio</span></span>

<span data-ttu-id="7f288-103">Les différents types de projets LINQ requièrent certaines références d’assembly et les espaces de noms importésC#(Visual Basic) ou les directives [using](../../../csharp/language-reference/keywords/using-directive.md) ().</span><span class="sxs-lookup"><span data-stu-id="7f288-103">The different types of LINQ projects require certain assembly references and imported namespaces (Visual Basic) or [using](../../../csharp/language-reference/keywords/using-directive.md) directives (C#).</span></span> <span data-ttu-id="7f288-104">La configuration minimale requise pour LINQ est une référence à *System. Core. dll* et `using` une directive <xref:System.Linq>pour.</span><span class="sxs-lookup"><span data-stu-id="7f288-104">The minimum requirement for LINQ is a reference to *System.Core.dll* and a `using` directive for <xref:System.Linq>.</span></span>

<span data-ttu-id="7f288-105">Ces exigences sont fournies par défaut si vous créez un projet C# d’application console dans Visual Studio 2017.</span><span class="sxs-lookup"><span data-stu-id="7f288-105">These requirements are supplied by default if you create a new C# console app project in Visual Studio 2017.</span></span> <span data-ttu-id="7f288-106">Si vous mettez à niveau un projet à partir d’une version antérieure de Visual Studio, vous devrez peut-être fournir manuellement ces références liées à LINQ.</span><span class="sxs-lookup"><span data-stu-id="7f288-106">If you're upgrading a project from an earlier version of Visual Studio, you might have to supply these LINQ-related references manually.</span></span>

<span data-ttu-id="7f288-107">LINQ to DataSet requiert deux références supplémentaires à *System. Data. dll* et *System. Data. DataSetExtensions. dll*.</span><span class="sxs-lookup"><span data-stu-id="7f288-107">LINQ to DataSet requires two additional references to *System.Data.dll* and *System.Data.DataSetExtensions.dll*.</span></span>

> [!NOTE]
> <span data-ttu-id="7f288-108">Si vous effectuez une génération à partir d’une invite de commandes, vous devez référencer manuellement les dll liées à LINQ dans *%ProgramFiles%\Reference Assemblies\Microsoft\Framework\v3.5*.</span><span class="sxs-lookup"><span data-stu-id="7f288-108">If you're building from a command prompt, you must manually reference the LINQ-related DLLs in *%ProgramFiles%\Reference Assemblies\Microsoft\Framework\v3.5*.</span></span>

## <a name="to-enable-linq-to-dataset-functionality"></a><span data-ttu-id="7f288-109">Pour activer les fonctionnalités LINQ to DataSet</span><span class="sxs-lookup"><span data-stu-id="7f288-109">To enable LINQ to DataSet functionality</span></span>

<span data-ttu-id="7f288-110">Procédez comme suit pour activer LINQ to DataSet fonctionnalité dans un projet existant.</span><span class="sxs-lookup"><span data-stu-id="7f288-110">Follow these steps to enable LINQ to DataSet functionality in an existing project.</span></span>

1. <span data-ttu-id="7f288-111">Ajoutez des références à **System. Core**, **System. Data**et **System. Data. DataSetExtensions**.</span><span class="sxs-lookup"><span data-stu-id="7f288-111">Add references to **System.Core**, **System.Data**, and **System.Data.DataSetExtensions**.</span></span>

   <span data-ttu-id="7f288-112">Dans **Explorateur de solutions**, cliquez avec le bouton droit sur le nœud **références** et sélectionnez **Ajouter une référence**.</span><span class="sxs-lookup"><span data-stu-id="7f288-112">In **Solution Explorer**, right-click on the **References** node and select **Add Reference**.</span></span> <span data-ttu-id="7f288-113">Dans la boîte de dialogue **Gestionnaire de références** , sélectionnez **System. Core**, **System. Data**et **System. Data. DataSetExtensions**.</span><span class="sxs-lookup"><span data-stu-id="7f288-113">In the **Reference Manager** dialog box, select **System.Core**, **System.Data**, and **System.Data.DataSetExtensions**.</span></span> <span data-ttu-id="7f288-114">Sélectionnez **OK**.</span><span class="sxs-lookup"><span data-stu-id="7f288-114">Select **OK**.</span></span>

1. <span data-ttu-id="7f288-115">Ajoutez des directives [using](../../../csharp/language-reference/keywords/using-directive.md) (ou des [instructions Imports](../../../visual-basic/language-reference/statements/imports-statement-net-namespace-and-type.md) dans Visual Basic) pour **System. Data** et **System. Linq**.</span><span class="sxs-lookup"><span data-stu-id="7f288-115">Add [using](../../../csharp/language-reference/keywords/using-directive.md) directives (or [Imports statements](../../../visual-basic/language-reference/statements/imports-statement-net-namespace-and-type.md) in Visual Basic) for **System.Data** and **System.Linq**.</span></span>

   ```csharp
   using System.Data;
   using System.Linq;
   ```

1. <span data-ttu-id="7f288-116">Si vous le souhaitez, `using` ajoutez une directive `Imports` (ou une instruction) pour **System. Data. Common** ou **System. Data. SqlClient**, selon la façon dont vous vous connectez à la base de données.</span><span class="sxs-lookup"><span data-stu-id="7f288-116">Optionally, add a `using` directive (or `Imports` statement) for **System.Data.Common** or **System.Data.SqlClient**, depending on how you connect to the database.</span></span>

## <a name="see-also"></a><span data-ttu-id="7f288-117">Voir aussi</span><span class="sxs-lookup"><span data-stu-id="7f288-117">See also</span></span>

- [<span data-ttu-id="7f288-118">Prise en main de LINQ to DataSet</span><span class="sxs-lookup"><span data-stu-id="7f288-118">Get started with LINQ to DataSet</span></span>](getting-started-linq-to-dataset.md)
