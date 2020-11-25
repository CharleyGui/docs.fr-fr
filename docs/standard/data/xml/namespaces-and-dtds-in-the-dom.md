---
title: Espaces de noms et DTD dans le DOM
ms.date: 03/30/2017
ms.assetid: 1e9b55c4-76ad-4f54-8d96-7ce4b4cf1e05
ms.openlocfilehash: 42bd30e7eea2ec0a3e1aa6846196c3280697efdf
ms.sourcegitcommit: d8020797a6657d0fbbdff362b80300815f682f94
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 11/24/2020
ms.locfileid: "95714547"
---
# <a name="namespaces-and-dtds-in-the-dom"></a><span data-ttu-id="d5287-102">Espaces de noms et DTD dans le DOM</span><span class="sxs-lookup"><span data-stu-id="d5287-102">Namespaces and DTDs in the DOM</span></span>

<span data-ttu-id="d5287-103">Les définitions de type de document (DTD) compliquent la prise en charge des espaces de noms.</span><span class="sxs-lookup"><span data-stu-id="d5287-103">Document type definitions (DTDs) complicate namespace support.</span></span> <span data-ttu-id="d5287-104">Par exemple, le code XML suivant contient des attributs par défaut, et un de ces noms comporte le signe deux-points.</span><span class="sxs-lookup"><span data-stu-id="d5287-104">For example, the following XML contains default attributes containing colons in their names.</span></span>  
  
```xml  
<!ATTLIST item x:id CDATA #IMPLIED>  
```  
  
 <span data-ttu-id="d5287-105">Voici les résolutions possibles si cette construction est autorisée :</span><span class="sxs-lookup"><span data-stu-id="d5287-105">The following are possible resolutions if this construct is allowed:</span></span>  
  
- <span data-ttu-id="d5287-106">`x:` est traité comme un préfixe d'espace de noms, mais il doit pouvoir être résolu à l'aide d'une déclaration d'espace de noms `xmlns:x`, qui doit également figurer dans la DTD.</span><span class="sxs-lookup"><span data-stu-id="d5287-106">The `x:` is treated as a namespace prefix, but this prefix must be resolvable using an `xmlns:x` namespace declaration, which must also exist somewhere in the DTD.</span></span> <span data-ttu-id="d5287-107">Il est incorrect de mapper ce préfixe à autre chose dans l'instance de document.</span><span class="sxs-lookup"><span data-stu-id="d5287-107">It is an error to map this prefix to something different in the instance document.</span></span>  
  
- <span data-ttu-id="d5287-108">`x:` est traité comme un préfixe d'espace de noms, mais il est toujours résolu dans le contexte des éléments d'instance.</span><span class="sxs-lookup"><span data-stu-id="d5287-108">The `x:` is treated as a namespace prefix, but this prefix is always resolved in the context of the instance elements.</span></span> <span data-ttu-id="d5287-109">Cela signifie que le préfixe peut en réalité être mappé à des URI (Uniform Resource Identifiers) d'espaces de noms différents en fonction de la portée d'espace de noms dans laquelle apparaît l'élément `item`.</span><span class="sxs-lookup"><span data-stu-id="d5287-109">This means the prefix could actually map to different namespace Uniform Resource Identifiers (URIs), depending on the namespace scope in which the `item` element appears.</span></span> <span data-ttu-id="d5287-110">Ce comportement est plus prévisible que dans le cas de la résolution décrite au point précédent, mais il implique d’autres ramifications compliquées dans la mesure où il nécessite la matérialisation des attributs par défaut.</span><span class="sxs-lookup"><span data-stu-id="d5287-110">This behavior is more predictable than the resolution given in the earlier bullet, but it has other complicated ramifications because it requires the default attributes be materialized.</span></span>  
  
- <span data-ttu-id="d5287-111">Le deux-points est ignoré car il figure dans une DTD et le nom de l'attribut est `x:y`, sans préfixe ni URI d'espace de noms.</span><span class="sxs-lookup"><span data-stu-id="d5287-111">The colon is ignored because it is in a DTD, and the name of the attribute is `x:y`, no prefix and no namespace URI.</span></span>  
  
- <span data-ttu-id="d5287-112">Le deux-points de l'attribut par défaut entraîne la levée d'une exception indiquant que les deux-points ne sont pas pris en charge dans les noms situés dans une DTD.</span><span class="sxs-lookup"><span data-stu-id="d5287-112">The colon in the default attribute throws an exception, saying that colons in names inside a DTD are not supported.</span></span> <span data-ttu-id="d5287-113">Cela aboutit à un comportement prévisible, mais qui empêche le chargement de la plupart des DTD publiées par le World Wide Web Consortium (W3C).</span><span class="sxs-lookup"><span data-stu-id="d5287-113">This results in a predictable behavior, but means you cannot load many of the World Wide Web Consortium (W3C) published DTDs.</span></span>  
  
- <span data-ttu-id="d5287-114">Quand l’utilisateur demande une validation DTD, la prise en charge des espaces de noms est désactivée pour le document tout entier.</span><span class="sxs-lookup"><span data-stu-id="d5287-114">When the user requests DTD validation, namespace support for the entire document is turned off.</span></span> <span data-ttu-id="d5287-115">Il est ensuite possible de charger des DTD W3C et cela donne lieu à un comportement prévisible.</span><span class="sxs-lookup"><span data-stu-id="d5287-115">This makes it possible to load W3C DTDs and results in a predictable behavior.</span></span>  
  
 <span data-ttu-id="d5287-116">Le langage XML dans Microsoft .NET Framework implémente la deuxième option pour optimiser la compatibilité W3C.</span><span class="sxs-lookup"><span data-stu-id="d5287-116">The XML in the Microsoft .NET Framework implements the second option for maximum W3C compatibility.</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="d5287-117">Voir aussi</span><span class="sxs-lookup"><span data-stu-id="d5287-117">See also</span></span>

- [<span data-ttu-id="d5287-118">DOM (Document Object Model) XML</span><span class="sxs-lookup"><span data-stu-id="d5287-118">XML Document Object Model (DOM)</span></span>](xml-document-object-model-dom.md)
