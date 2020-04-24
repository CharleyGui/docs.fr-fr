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
ms.openlocfilehash: bea6ca24ea6da9000267e754d52fe0ca152f7d7f
ms.sourcegitcommit: eff6adb61852369ab690f3f047818c90580e7eb1
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 10/07/2019
ms.locfileid: "72005231"
---
# <a name="-removeintchecks"></a><span data-ttu-id="ae805-102">-removeintchecks</span><span class="sxs-lookup"><span data-stu-id="ae805-102">-removeintchecks</span></span>
<span data-ttu-id="ae805-103">Active ou désactive la vérification des erreurs de dépassement de capacité pour les opérations sur les entiers.</span><span class="sxs-lookup"><span data-stu-id="ae805-103">Turns overflow-error checking for integer operations on or off.</span></span>  
  
## <a name="syntax"></a><span data-ttu-id="ae805-104">Syntaxe</span><span class="sxs-lookup"><span data-stu-id="ae805-104">Syntax</span></span>  
  
```console  
-removeintchecks[+ | -]  
```  
  
## <a name="arguments"></a><span data-ttu-id="ae805-105">Arguments</span><span class="sxs-lookup"><span data-stu-id="ae805-105">Arguments</span></span>  
  
|<span data-ttu-id="ae805-106">Terme</span><span class="sxs-lookup"><span data-stu-id="ae805-106">Term</span></span>|<span data-ttu-id="ae805-107">Définition</span><span class="sxs-lookup"><span data-stu-id="ae805-107">Definition</span></span>|  
|---|---|  
|<span data-ttu-id="ae805-108">`+` &#124; `-`</span><span class="sxs-lookup"><span data-stu-id="ae805-108">`+` &#124; `-`</span></span>|<span data-ttu-id="ae805-109">Facultatif.</span><span class="sxs-lookup"><span data-stu-id="ae805-109">Optional.</span></span> <span data-ttu-id="ae805-110">Avec `-removeintchecks-` l’option, le compilateur vérifie tous les calculs d’entiers pour les erreurs de dépassement de capacité.</span><span class="sxs-lookup"><span data-stu-id="ae805-110">The `-removeintchecks-` option causes the compiler to check all integer calculations for overflow errors.</span></span> <span data-ttu-id="ae805-111">Par défaut, il s’agit de `-removeintchecks-`.</span><span class="sxs-lookup"><span data-stu-id="ae805-111">The default is `-removeintchecks-`.</span></span><br /><br /> <span data-ttu-id="ae805-112">Le `-removeintchecks` fait `-removeintchecks+` de spécifier ou d’empêcher la vérification des erreurs et peut accélérer le calcul des entiers.</span><span class="sxs-lookup"><span data-stu-id="ae805-112">Specifying `-removeintchecks` or `-removeintchecks+` prevents error checking and can make integer calculations faster.</span></span> <span data-ttu-id="ae805-113">Toutefois, sans vérification des erreurs, et si les capacités des types de données sont dépassées, des résultats incorrects peuvent être stockés sans déclencher d’erreur.</span><span class="sxs-lookup"><span data-stu-id="ae805-113">However, without error checking, and if data type capacities are overflowed, incorrect results may be stored without raising an error.</span></span>|  
  
|<span data-ttu-id="ae805-114">Pour définir-removeintchecks (dans l’environnement de développement intégré Visual Studio</span><span class="sxs-lookup"><span data-stu-id="ae805-114">To set -removeintchecks in the Visual Studio integrated development environment</span></span>|  
|---|  
|<span data-ttu-id="ae805-115">1. Sélectionnez un projet dans **Explorateur de solutions**.</span><span class="sxs-lookup"><span data-stu-id="ae805-115">1.  Have a project selected in **Solution Explorer**.</span></span> <span data-ttu-id="ae805-116">Dans le menu **Projet** , cliquez sur **Propriétés**.</span><span class="sxs-lookup"><span data-stu-id="ae805-116">On the **Project** menu, click **Properties**.</span></span> <br /><span data-ttu-id="ae805-117">2. cliquez sur l’onglet **compiler** .</span><span class="sxs-lookup"><span data-stu-id="ae805-117">2.  Click the **Compile** tab.</span></span><br /><span data-ttu-id="ae805-118">3. cliquez sur le bouton **avancé** .</span><span class="sxs-lookup"><span data-stu-id="ae805-118">3.  Click the **Advanced** button.</span></span><br /><span data-ttu-id="ae805-119">4. modifiez la valeur de la zone supprimer les contrôles de dépassement sur les **entiers** .</span><span class="sxs-lookup"><span data-stu-id="ae805-119">4.  Modify the value of the **Remove integer overflow checks** box.</span></span>|  
  
## <a name="example"></a><span data-ttu-id="ae805-120">Exemple</span><span class="sxs-lookup"><span data-stu-id="ae805-120">Example</span></span>  
 <span data-ttu-id="ae805-121">Le code suivant compile `Test.vb` et désactive la vérification des erreurs de dépassement sur les entiers.</span><span class="sxs-lookup"><span data-stu-id="ae805-121">The following code compiles `Test.vb` and turns off integer overflow-error checking.</span></span>  
  
```console
vbc -removeintchecks+ test.vb  
```  
  
## <a name="see-also"></a><span data-ttu-id="ae805-122">Voir aussi</span><span class="sxs-lookup"><span data-stu-id="ae805-122">See also</span></span>

- [<span data-ttu-id="ae805-123">Compilateur de ligne de commande de Visual Basic</span><span class="sxs-lookup"><span data-stu-id="ae805-123">Visual Basic Command-Line Compiler</span></span>](../../../visual-basic/reference/command-line-compiler/index.md)
- [<span data-ttu-id="ae805-124">Exemples de lignes de commande de compilation</span><span class="sxs-lookup"><span data-stu-id="ae805-124">Sample Compilation Command Lines</span></span>](../../../visual-basic/reference/command-line-compiler/sample-compilation-command-lines.md)
