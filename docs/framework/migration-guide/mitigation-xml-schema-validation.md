---
title: 'Atténuation : validation du schéma XML'
ms.date: 03/30/2017
dev_langs:
- csharp
- vb
ms.assetid: b73dd4f4-f2dc-47a2-9425-3896e92321fb
author: rpetrusha
ms.author: ronpet
ms.openlocfilehash: 36f9475a978ddf7253833e6c3372049d24502f95
ms.sourcegitcommit: 621a5f6df00152006160987395b93b5b55f7ffcd
ms.translationtype: HT
ms.contentlocale: fr-FR
ms.lasthandoff: 05/29/2019
ms.locfileid: "66300584"
---
# <a name="mitigation-xml-schema-validation"></a><span data-ttu-id="8b8aa-102">Atténuation : validation du schéma XML</span><span class="sxs-lookup"><span data-stu-id="8b8aa-102">Mitigation: XML Schema Validation</span></span>
<span data-ttu-id="8b8aa-103">Dans .NET Framework 4.6, la validation de schéma XSD détecte une violation de contrainte unique si une clé composée est utilisée et qu’une clé est vide.</span><span class="sxs-lookup"><span data-stu-id="8b8aa-103">In the .NET Framework 4.6, XSD schema validation detects a violation of the unique constraint if a compound key is used and one key is empty.</span></span>  
  
## <a name="impact"></a><span data-ttu-id="8b8aa-104">Impact</span><span class="sxs-lookup"><span data-stu-id="8b8aa-104">Impact</span></span>  
 <span data-ttu-id="8b8aa-105">L'impact de cette modification devrait être minime : selon la spécification de schéma, une erreur de validation de schéma est attendue si `xsd:unique` est enfreinte par l'utilisation d'une clé composée avec une clé vide.</span><span class="sxs-lookup"><span data-stu-id="8b8aa-105">The impact of this change should be minimal: based on the schema specification, a schema validation error is expected if `xsd:unique` is violated by using a compound key with an empty key.</span></span>  
  
## <a name="mitigation"></a><span data-ttu-id="8b8aa-106">Atténuation</span><span class="sxs-lookup"><span data-stu-id="8b8aa-106">Mitigation</span></span>  
 <span data-ttu-id="8b8aa-107">Le fait qu'une erreur de validation de schéma soit détectée ou pas si une clé composée a une clé vide est une fonctionnalité que vous pouvez configurer :</span><span class="sxs-lookup"><span data-stu-id="8b8aa-107">Whether a schema validation error is detected if a compound key has one empty key is a configurable feature:</span></span>  
  
- <span data-ttu-id="8b8aa-108">Depuis les applications qui ciblent .NET Framework 4.6, la détection de l’erreur de validation de schéma est activée par défaut ; néanmoins, il est possible de la refuser afin que l’erreur de validation de schéma ne soit pas détectée.</span><span class="sxs-lookup"><span data-stu-id="8b8aa-108">Starting with the apps that target the .NET Framework 4.6, detection of the schema validation error is enabled by default; however, it is possible to opt out of it, so that the schema validation error will not be detected.</span></span>  
  
- <span data-ttu-id="8b8aa-109">Dans les applications qui s’exécutent sous .NET Framework 4.6, mais ciblent .NET Framework 4.5.2 et versions antérieures, la détection de l’erreur de validation de schéma n’est pas activée par défaut ; néanmoins, il est possible de l’activer afin que l’erreur de validation de schéma soit détectée.</span><span class="sxs-lookup"><span data-stu-id="8b8aa-109">In apps that run under the .NET Framework 4.6 but target the .NET Framework 4.5.2 and earlier versions, a schema validation error is not detected by default; however, it is possible to opt into it, so that the schema validation error will be detected.</span></span>  
  
 <span data-ttu-id="8b8aa-110">Ce comportement peut être configuré en utilisant la classe <xref:System.AppContext> pour définir la valeur du commutateur `System.Xml.IgnoreEmptyKeySequences`.</span><span class="sxs-lookup"><span data-stu-id="8b8aa-110">This behavior can be configured by using the <xref:System.AppContext> class to define the value of the `System.Xml.IgnoreEmptyKeySequences` switch.</span></span> <span data-ttu-id="8b8aa-111">Comme la valeur par défaut du commutateur est `false` (les séquences de touches vides ne sont pas ignorées), les applications qui ciblent .NET Framework 4.6 peuvent désactiver le comportement en utilisant le code suivant pour définir le commutateur avec la valeur `true` :</span><span class="sxs-lookup"><span data-stu-id="8b8aa-111">Because the switch's default value is `false` (empty key sequences are not ignored), apps that target the .NET Framework 4.6 can opt out of the behavior by using the following code to set the switch's value to `true`:</span></span>  
  
 [!code-csharp[AppCompat.IgnoreEmptyKeySequences#1](../../../samples/snippets/csharp/VS_Snippets_CLR/appcompat.ignoreemptykeysequences/cs/program.cs#1)]
 [!code-vb[AppCompat.IgnoreEmptyKeySequences#1](../../../samples/snippets/visualbasic/VS_Snippets_CLR/appcompat.ignoreemptykeysequences/vb/module1.vb#1)]  
  
 <span data-ttu-id="8b8aa-112">Pour les applications qui ciblent .NET Framework 4.5.2 et versions antérieures, comme la valeur par défaut du commutateur est `true` (les séquences de touches vides sont ignorées), il est possible de garantir qu’une clé composée avec une clé vide génère bel et bien une erreur de validation de schéma en utilisant le code suivant pour définir le commutateur avec la valeur `false`.</span><span class="sxs-lookup"><span data-stu-id="8b8aa-112">For apps that target the .NET Framework 4.5.2 and earlier versions, because the switch's default value is `true` (empty key sequences are ignored), it is possible to ensure that a compound key with an empty key does generate a schema validation error by using the following code to set the switch's value to `false`.</span></span>  
  
 [!code-csharp[AppCompat.IgnoreEmptyKeySequences#2](../../../samples/snippets/csharp/VS_Snippets_CLR/appcompat.ignoreemptykeysequences/cs/program.cs#2)]
 [!code-vb[AppCompat.IgnoreEmptyKeySequences#2](../../../samples/snippets/visualbasic/VS_Snippets_CLR/appcompat.ignoreemptykeysequences/vb/module1.vb#2)]  
  
## <a name="see-also"></a><span data-ttu-id="8b8aa-113">Voir aussi</span><span class="sxs-lookup"><span data-stu-id="8b8aa-113">See also</span></span>

- [<span data-ttu-id="8b8aa-114">Modifications de reciblage</span><span class="sxs-lookup"><span data-stu-id="8b8aa-114">Retargeting Changes</span></span>](../../../docs/framework/migration-guide/retargeting-changes-in-the-net-framework-4-6.md)
