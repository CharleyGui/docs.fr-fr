---
title: Limites
ms.date: 07/20/2015
helpviewer_keywords:
- limits
- limitations [Visual Basic]
- limitations
- limits, Visual Basic code
- Visual Basic code, limitations
ms.assetid: cf1646b7-5d24-48c6-9616-bda8a4849d91
ms.openlocfilehash: abe4acd5850aa6065bf4f6fd41bc610ede7ad13f
ms.sourcegitcommit: bf5c5850654187705bc94cc40ebfb62fe346ab02
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 09/23/2020
ms.locfileid: "91097954"
---
# <a name="visual-basic-limitations"></a><span data-ttu-id="0cede-102">Restrictions liées à Visual Basic</span><span class="sxs-lookup"><span data-stu-id="0cede-102">Visual Basic Limitations</span></span>

<span data-ttu-id="0cede-103">Les versions antérieures de Visual Basic des limites appliquées dans le code, telles que la longueur des noms de variables, le nombre de variables autorisées dans les modules et la taille du module.</span><span class="sxs-lookup"><span data-stu-id="0cede-103">Earlier versions of Visual Basic enforced boundaries in code, such as the length of variable names, the number of variables allowed in modules, and module size.</span></span> <span data-ttu-id="0cede-104">Dans Visual Basic .NET, ces restrictions ont été assouplies, ce qui vous offre une plus grande liberté dans l’écriture et l’organisation de votre code.</span><span class="sxs-lookup"><span data-stu-id="0cede-104">In Visual Basic .NET, these restrictions have been relaxed, giving you greater freedom in writing and arranging your code.</span></span>  
  
 <span data-ttu-id="0cede-105">Les limites physiques dépendent davantage de la mémoire au moment de l’exécution que des considérations relatives à la compilation.</span><span class="sxs-lookup"><span data-stu-id="0cede-105">Physical limits are dependent more on run-time memory than on compile-time considerations.</span></span> <span data-ttu-id="0cede-106">Si vous utilisez des pratiques de programmation prudentes et que vous divisez des applications volumineuses en plusieurs classes et modules, il y a très peu de chance de rencontrer une limitation de Visual Basic interne.</span><span class="sxs-lookup"><span data-stu-id="0cede-106">If you use prudent programming practices, and divide large applications into multiple classes and modules, then there is very little chance of encountering an internal Visual Basic limitation.</span></span>  
  
 <span data-ttu-id="0cede-107">Voici quelques-unes des limitations que vous pouvez rencontrer dans les cas extrêmes :</span><span class="sxs-lookup"><span data-stu-id="0cede-107">The following are some limitations that you might encounter in extreme cases:</span></span>  
  
- <span data-ttu-id="0cede-108">**Longueur du nom.**</span><span class="sxs-lookup"><span data-stu-id="0cede-108">**Name Length.**</span></span> <span data-ttu-id="0cede-109">Il y a un nombre maximal de caractères pour le nom de chaque élément de programmation déclaré.</span><span class="sxs-lookup"><span data-stu-id="0cede-109">There is a maximum number of characters for the name of every declared programming element.</span></span> <span data-ttu-id="0cede-110">Cette valeur maximale s’applique à une chaîne de qualification entière si le nom d’élément est qualifié.</span><span class="sxs-lookup"><span data-stu-id="0cede-110">This maximum applies to an entire qualification string if the element name is qualified.</span></span> <span data-ttu-id="0cede-111">Consultez [Declared Element Names](../language-features/declared-elements/declared-element-names.md).</span><span class="sxs-lookup"><span data-stu-id="0cede-111">See [Declared Element Names](../language-features/declared-elements/declared-element-names.md).</span></span>  
  
- <span data-ttu-id="0cede-112">**Longueur de la ligne.**</span><span class="sxs-lookup"><span data-stu-id="0cede-112">**Line Length.**</span></span> <span data-ttu-id="0cede-113">Il y a un maximum de 65535 caractères dans une ligne physique de code source.</span><span class="sxs-lookup"><span data-stu-id="0cede-113">There is a maximum of 65535 characters in a physical line of source code.</span></span> <span data-ttu-id="0cede-114">La ligne de code source logique peut être plus longue si vous utilisez des caractères de continuation de ligne.</span><span class="sxs-lookup"><span data-stu-id="0cede-114">The logical source code line can be longer if you use line continuation characters.</span></span> <span data-ttu-id="0cede-115">Consultez [Comment : arrêter et combiner des instructions dans le code](how-to-break-and-combine-statements-in-code.md).</span><span class="sxs-lookup"><span data-stu-id="0cede-115">See [How to: Break and Combine Statements in Code](how-to-break-and-combine-statements-in-code.md).</span></span>  
  
- <span data-ttu-id="0cede-116">**Dimensions du tableau.**</span><span class="sxs-lookup"><span data-stu-id="0cede-116">**Array Dimensions.**</span></span> <span data-ttu-id="0cede-117">Vous pouvez déclarer un nombre maximal de dimensions pour un tableau.</span><span class="sxs-lookup"><span data-stu-id="0cede-117">There is a maximum number of dimensions you can declare for an array.</span></span> <span data-ttu-id="0cede-118">Cela limite le nombre d’index que vous pouvez utiliser pour spécifier un élément de tableau.</span><span class="sxs-lookup"><span data-stu-id="0cede-118">This limits how many indexes you can use to specify an array element.</span></span> <span data-ttu-id="0cede-119">Consultez [dimensions de tableau dans Visual Basic](../language-features/arrays/array-dimensions.md).</span><span class="sxs-lookup"><span data-stu-id="0cede-119">See [Array Dimensions in Visual Basic](../language-features/arrays/array-dimensions.md).</span></span>  
  
- <span data-ttu-id="0cede-120">**Longueur de chaîne.**</span><span class="sxs-lookup"><span data-stu-id="0cede-120">**String Length.**</span></span> <span data-ttu-id="0cede-121">Il y a un nombre maximal de caractères Unicode que vous pouvez stocker dans une chaîne unique.</span><span class="sxs-lookup"><span data-stu-id="0cede-121">There is a maximum number of Unicode characters you can store in a single string.</span></span> <span data-ttu-id="0cede-122">Consultez [type de données String](../../language-reference/data-types/string-data-type.md).</span><span class="sxs-lookup"><span data-stu-id="0cede-122">See [String Data Type](../../language-reference/data-types/string-data-type.md).</span></span>  
  
- <span data-ttu-id="0cede-123">**Longueur de la chaîne d’environnement.**</span><span class="sxs-lookup"><span data-stu-id="0cede-123">**Environment String Length.**</span></span> <span data-ttu-id="0cede-124">Il y a un maximum de 32768 caractères pour toute chaîne d’environnement utilisée comme argument de ligne de commande.</span><span class="sxs-lookup"><span data-stu-id="0cede-124">There is a maximum of 32768 characters for any environment string used as a command-line argument.</span></span> <span data-ttu-id="0cede-125">Il s’agit d’une limitation sur toutes les plateformes.</span><span class="sxs-lookup"><span data-stu-id="0cede-125">This is a limitation on all platforms.</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="0cede-126">Voir aussi</span><span class="sxs-lookup"><span data-stu-id="0cede-126">See also</span></span>

- [<span data-ttu-id="0cede-127">Structure de programme et conventions de code</span><span class="sxs-lookup"><span data-stu-id="0cede-127">Program Structure and Code Conventions</span></span>](program-structure-and-code-conventions.md)
- [<span data-ttu-id="0cede-128">Conventions d'affectation de noms Visual Basic</span><span class="sxs-lookup"><span data-stu-id="0cede-128">Visual Basic Naming Conventions</span></span>](naming-conventions.md)
