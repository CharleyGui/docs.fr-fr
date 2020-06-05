---
title: -removeintchecks
ms.date: 03/13/2018
f1_keywords:
- removeintchecks
- -removeintchecks
helpviewer_keywords:
- removeintchecks compiler option [Visual Basic]
- /removeintchecks compiler option [Visual Basic]
- -removeintchecks compiler option [Visual Basic]
ms.assetid: c1835bd5-1e38-4fba-bd2f-6984774765d4
ms.openlocfilehash: ec4722cb7088819dae95ca1b7cbc1469d957a7aa
ms.sourcegitcommit: f8c270376ed905f6a8896ce0fe25b4f4b38ff498
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 06/04/2020
ms.locfileid: "84400472"
---
# <a name="-removeintchecks"></a><span data-ttu-id="402a3-102">-removeintchecks</span><span class="sxs-lookup"><span data-stu-id="402a3-102">-removeintchecks</span></span>
<span data-ttu-id="402a3-103">Active ou désactive la vérification des erreurs de dépassement de capacité pour les opérations sur les entiers.</span><span class="sxs-lookup"><span data-stu-id="402a3-103">Turns overflow-error checking for integer operations on or off.</span></span>  
  
## <a name="syntax"></a><span data-ttu-id="402a3-104">Syntaxe</span><span class="sxs-lookup"><span data-stu-id="402a3-104">Syntax</span></span>  
  
```console  
-removeintchecks[+ | -]  
```  
  
## <a name="arguments"></a><span data-ttu-id="402a3-105">Arguments</span><span class="sxs-lookup"><span data-stu-id="402a3-105">Arguments</span></span>  
  
|<span data-ttu-id="402a3-106">Terme</span><span class="sxs-lookup"><span data-stu-id="402a3-106">Term</span></span>|<span data-ttu-id="402a3-107">Définition</span><span class="sxs-lookup"><span data-stu-id="402a3-107">Definition</span></span>|  
|---|---|  
|<span data-ttu-id="402a3-108">`+` &#124; `-`</span><span class="sxs-lookup"><span data-stu-id="402a3-108">`+` &#124; `-`</span></span>|<span data-ttu-id="402a3-109">Facultatif.</span><span class="sxs-lookup"><span data-stu-id="402a3-109">Optional.</span></span> <span data-ttu-id="402a3-110">`-removeintchecks-`Avec l’option, le compilateur vérifie tous les calculs d’entiers pour les erreurs de dépassement de capacité.</span><span class="sxs-lookup"><span data-stu-id="402a3-110">The `-removeintchecks-` option causes the compiler to check all integer calculations for overflow errors.</span></span> <span data-ttu-id="402a3-111">Par défaut, il s’agit de `-removeintchecks-`.</span><span class="sxs-lookup"><span data-stu-id="402a3-111">The default is `-removeintchecks-`.</span></span><br /><br /> <span data-ttu-id="402a3-112">Le `-removeintchecks` fait de spécifier ou d' `-removeintchecks+` empêcher la vérification des erreurs et peut accélérer le calcul des entiers.</span><span class="sxs-lookup"><span data-stu-id="402a3-112">Specifying `-removeintchecks` or `-removeintchecks+` prevents error checking and can make integer calculations faster.</span></span> <span data-ttu-id="402a3-113">Toutefois, sans vérification des erreurs, et si les capacités des types de données sont dépassées, des résultats incorrects peuvent être stockés sans déclencher d’erreur.</span><span class="sxs-lookup"><span data-stu-id="402a3-113">However, without error checking, and if data type capacities are overflowed, incorrect results may be stored without raising an error.</span></span>|  
  
|<span data-ttu-id="402a3-114">Pour définir-removeintchecks (dans l’environnement de développement intégré Visual Studio</span><span class="sxs-lookup"><span data-stu-id="402a3-114">To set -removeintchecks in the Visual Studio integrated development environment</span></span>|  
|---|  
|<span data-ttu-id="402a3-115">1. Sélectionnez un projet dans **Explorateur de solutions**.</span><span class="sxs-lookup"><span data-stu-id="402a3-115">1.  Have a project selected in **Solution Explorer**.</span></span> <span data-ttu-id="402a3-116">Dans le menu **Projet** , cliquez sur **Propriétés**.</span><span class="sxs-lookup"><span data-stu-id="402a3-116">On the **Project** menu, click **Properties**.</span></span> <br /><span data-ttu-id="402a3-117">2. cliquez sur l’onglet **compiler** .</span><span class="sxs-lookup"><span data-stu-id="402a3-117">2.  Click the **Compile** tab.</span></span><br /><span data-ttu-id="402a3-118">3. cliquez sur le bouton **avancé** .</span><span class="sxs-lookup"><span data-stu-id="402a3-118">3.  Click the **Advanced** button.</span></span><br /><span data-ttu-id="402a3-119">4. modifiez la valeur de la zone supprimer les contrôles de dépassement sur les **entiers** .</span><span class="sxs-lookup"><span data-stu-id="402a3-119">4.  Modify the value of the **Remove integer overflow checks** box.</span></span>|  
  
## <a name="example"></a><span data-ttu-id="402a3-120">Exemple</span><span class="sxs-lookup"><span data-stu-id="402a3-120">Example</span></span>  
 <span data-ttu-id="402a3-121">Le code suivant compile `Test.vb` et désactive la vérification des erreurs de dépassement sur les entiers.</span><span class="sxs-lookup"><span data-stu-id="402a3-121">The following code compiles `Test.vb` and turns off integer overflow-error checking.</span></span>  
  
```console
vbc -removeintchecks+ test.vb  
```  
  
## <a name="see-also"></a><span data-ttu-id="402a3-122">Voir aussi</span><span class="sxs-lookup"><span data-stu-id="402a3-122">See also</span></span>

- [<span data-ttu-id="402a3-123">Compilateur de ligne de commande de Visual Basic</span><span class="sxs-lookup"><span data-stu-id="402a3-123">Visual Basic Command-Line Compiler</span></span>](index.md)
- [<span data-ttu-id="402a3-124">Exemples de lignes de commande de compilation</span><span class="sxs-lookup"><span data-stu-id="402a3-124">Sample Compilation Command Lines</span></span>](sample-compilation-command-lines.md)
