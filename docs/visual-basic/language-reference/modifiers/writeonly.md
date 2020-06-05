---
title: WriteOnly
ms.date: 07/20/2015
f1_keywords:
- WriteOnly
- vb.WriteOnly
helpviewer_keywords:
- write-only properties
- WriteOnly keyword [Visual Basic]
- sensitive data, protecting
- properties [Visual Basic], write-only
- sensitive data
ms.assetid: 488d2899-b09f-4cee-92f0-6f9f9fc4f944
ms.openlocfilehash: a9fa0a3a23561215d6ff122bc8e609b68ca6fc30
ms.sourcegitcommit: f8c270376ed905f6a8896ce0fe25b4f4b38ff498
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 06/04/2020
ms.locfileid: "84386632"
---
# <a name="writeonly-visual-basic"></a><span data-ttu-id="45b23-102">WriteOnly (Visual Basic)</span><span class="sxs-lookup"><span data-stu-id="45b23-102">WriteOnly (Visual Basic)</span></span>
<span data-ttu-id="45b23-103">Spécifie qu’une propriété peut être écrite mais pas lue.</span><span class="sxs-lookup"><span data-stu-id="45b23-103">Specifies that a property can be written but not read.</span></span>  
  
## <a name="remarks"></a><span data-ttu-id="45b23-104">Notes</span><span class="sxs-lookup"><span data-stu-id="45b23-104">Remarks</span></span>  
  
## <a name="rules"></a><span data-ttu-id="45b23-105">Règles</span><span class="sxs-lookup"><span data-stu-id="45b23-105">Rules</span></span>  
 <span data-ttu-id="45b23-106">**Contexte de déclaration.**</span><span class="sxs-lookup"><span data-stu-id="45b23-106">**Declaration Context.**</span></span> <span data-ttu-id="45b23-107">Vous pouvez utiliser `WriteOnly` seulement au niveau du module.</span><span class="sxs-lookup"><span data-stu-id="45b23-107">You can use `WriteOnly` only at module level.</span></span> <span data-ttu-id="45b23-108">Cela signifie que le contexte de déclaration pour une `WriteOnly` propriété doit être une classe, une structure ou un module, et ne peut pas être un fichier source, un espace de noms ou une procédure.</span><span class="sxs-lookup"><span data-stu-id="45b23-108">This means the declaration context for a `WriteOnly` property must be a class, structure, or module, and cannot be a source file, namespace, or procedure.</span></span>  
  
 <span data-ttu-id="45b23-109">Vous pouvez déclarer une propriété en tant que `WriteOnly` , mais pas en tant que variable.</span><span class="sxs-lookup"><span data-stu-id="45b23-109">You can declare a property as `WriteOnly`, but not a variable.</span></span>  
  
## <a name="when-to-use-writeonly"></a><span data-ttu-id="45b23-110">Quand utiliser WriteOnly</span><span class="sxs-lookup"><span data-stu-id="45b23-110">When to Use WriteOnly</span></span>  
 <span data-ttu-id="45b23-111">Parfois, vous souhaitez que le code de consommation soit en mesure de définir une valeur, mais pas de le découvrir.</span><span class="sxs-lookup"><span data-stu-id="45b23-111">Sometimes you want the consuming code to be able to set a value but not discover what it is.</span></span> <span data-ttu-id="45b23-112">Par exemple, les données sensibles, telles qu’un numéro d’enregistrement social ou un mot de passe, doivent être protégées contre tout composant qui n’a pas été défini.</span><span class="sxs-lookup"><span data-stu-id="45b23-112">For example, sensitive data, such as a social registration number or a password, needs to be protected from access by any component that did not set it.</span></span> <span data-ttu-id="45b23-113">Dans ce cas, vous pouvez utiliser une `WriteOnly` propriété pour définir la valeur.</span><span class="sxs-lookup"><span data-stu-id="45b23-113">In these cases, you can use a `WriteOnly` property to set the value.</span></span>  
  
> [!IMPORTANT]
> <span data-ttu-id="45b23-114">Lorsque vous définissez et utilisez une `WriteOnly` propriété, tenez compte des mesures de protection supplémentaires suivantes :</span><span class="sxs-lookup"><span data-stu-id="45b23-114">When you define and use a `WriteOnly` property, consider the following additional protective measures:</span></span>  
  
- <span data-ttu-id="45b23-115">**Substitution.**</span><span class="sxs-lookup"><span data-stu-id="45b23-115">**Overriding.**</span></span> <span data-ttu-id="45b23-116">Si la propriété est membre d’une classe, autorisez-la comme valeur par défaut [NotOverridable](notoverridable.md)et ne la déclarez pas `Overridable` ou `MustOverride` .</span><span class="sxs-lookup"><span data-stu-id="45b23-116">If the property is a member of a class, allow it to default to [NotOverridable](notoverridable.md), and do not declare it `Overridable` or `MustOverride`.</span></span> <span data-ttu-id="45b23-117">Cela empêche une classe dérivée d’accéder à un accès indésirable par le biais d’une substitution.</span><span class="sxs-lookup"><span data-stu-id="45b23-117">This prevents a derived class from making undesired access through an override.</span></span>  
  
- <span data-ttu-id="45b23-118">**Niveau d’accès.**</span><span class="sxs-lookup"><span data-stu-id="45b23-118">**Access Level.**</span></span> <span data-ttu-id="45b23-119">Si vous conservez les données sensibles de la propriété dans une ou plusieurs variables, déclarez-les comme [privées](private.md) afin qu’aucun autre code ne puisse y accéder.</span><span class="sxs-lookup"><span data-stu-id="45b23-119">If you hold the property's sensitive data in one or more variables, declare them [Private](private.md) so that no other code can access them.</span></span>  
  
- <span data-ttu-id="45b23-120">**Chiffre.**</span><span class="sxs-lookup"><span data-stu-id="45b23-120">**Encryption.**</span></span> <span data-ttu-id="45b23-121">Stockez toutes les données sensibles au format chiffré plutôt qu’en texte brut.</span><span class="sxs-lookup"><span data-stu-id="45b23-121">Store all sensitive data in encrypted form rather than in plain text.</span></span> <span data-ttu-id="45b23-122">Si du code malveillant parvient à accéder à cette zone de mémoire, il est plus difficile d’utiliser les données.</span><span class="sxs-lookup"><span data-stu-id="45b23-122">If malicious code somehow gains access to that area of memory, it is more difficult to make use of the data.</span></span> <span data-ttu-id="45b23-123">Le chiffrement est également utile s’il est nécessaire de sérialiser les données sensibles.</span><span class="sxs-lookup"><span data-stu-id="45b23-123">Encryption is also useful if it is necessary to serialize the sensitive data.</span></span>  
  
- <span data-ttu-id="45b23-124">**La réinitialisation.**</span><span class="sxs-lookup"><span data-stu-id="45b23-124">**Resetting.**</span></span> <span data-ttu-id="45b23-125">Lorsque la classe, la structure ou le module définissant la propriété est terminé, réinitialisez les données sensibles aux valeurs par défaut ou à d’autres valeurs non significatives.</span><span class="sxs-lookup"><span data-stu-id="45b23-125">When the class, structure, or module defining the property is being terminated, reset the sensitive data to default values or to other meaningless values.</span></span> <span data-ttu-id="45b23-126">Cela offre une protection supplémentaire lorsque cette zone de mémoire est libérée pour un accès général.</span><span class="sxs-lookup"><span data-stu-id="45b23-126">This gives extra protection when that area of memory is freed for general access.</span></span>  
  
- <span data-ttu-id="45b23-127">**Persistance.**</span><span class="sxs-lookup"><span data-stu-id="45b23-127">**Persistence.**</span></span> <span data-ttu-id="45b23-128">Ne conservez pas les données sensibles, par exemple sur le disque, si vous pouvez les éviter.</span><span class="sxs-lookup"><span data-stu-id="45b23-128">Do not persist any sensitive data, for example on disk, if you can avoid it.</span></span> <span data-ttu-id="45b23-129">En outre, n’écrivez pas de données sensibles dans le presse-papiers.</span><span class="sxs-lookup"><span data-stu-id="45b23-129">Also, do not write any sensitive data to the Clipboard.</span></span>  
  
 <span data-ttu-id="45b23-130">Le `WriteOnly` modificateur peut être utilisé dans ce contexte :</span><span class="sxs-lookup"><span data-stu-id="45b23-130">The `WriteOnly` modifier can be used in this context:</span></span>  
  
 [<span data-ttu-id="45b23-131">Property Statement</span><span class="sxs-lookup"><span data-stu-id="45b23-131">Property Statement</span></span>](../statements/property-statement.md)  
  
## <a name="see-also"></a><span data-ttu-id="45b23-132">Voir aussi</span><span class="sxs-lookup"><span data-stu-id="45b23-132">See also</span></span>

- [<span data-ttu-id="45b23-133">Seulement</span><span class="sxs-lookup"><span data-stu-id="45b23-133">ReadOnly</span></span>](readonly.md)
- [<span data-ttu-id="45b23-134">Privé</span><span class="sxs-lookup"><span data-stu-id="45b23-134">Private</span></span>](private.md)
- [<span data-ttu-id="45b23-135">Mots clés</span><span class="sxs-lookup"><span data-stu-id="45b23-135">Keywords</span></span>](../keywords/index.md)
