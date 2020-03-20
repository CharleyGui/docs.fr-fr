---
title: 'Atténuation : Validation du schéma XML'
ms.date: 03/30/2017
dev_langs:
- csharp
- vb
ms.assetid: b73dd4f4-f2dc-47a2-9425-3896e92321fb
ms.openlocfilehash: 99cc1eae08697909d89e5c1e46cd604c7da543bc
ms.sourcegitcommit: 7588136e355e10cbc2582f389c90c127363c02a5
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 03/15/2020
ms.locfileid: "73457742"
---
# <a name="mitigation-xml-schema-validation"></a><span data-ttu-id="aeda6-102">Atténuation : Validation du schéma XML</span><span class="sxs-lookup"><span data-stu-id="aeda6-102">Mitigation: XML Schema Validation</span></span>
<span data-ttu-id="aeda6-103">Dans .NET Framework 4.6, la validation de schéma XSD détecte une violation de contrainte unique si une clé composée est utilisée et qu’une clé est vide.</span><span class="sxs-lookup"><span data-stu-id="aeda6-103">In the .NET Framework 4.6, XSD schema validation detects a violation of the unique constraint if a compound key is used and one key is empty.</span></span>  
  
## <a name="impact"></a><span data-ttu-id="aeda6-104">Impact</span><span class="sxs-lookup"><span data-stu-id="aeda6-104">Impact</span></span>  
 <span data-ttu-id="aeda6-105">L'impact de cette modification devrait être minime : selon la spécification de schéma, une erreur de validation de schéma est attendue si `xsd:unique` est enfreinte par l'utilisation d'une clé composée avec une clé vide.</span><span class="sxs-lookup"><span data-stu-id="aeda6-105">The impact of this change should be minimal: based on the schema specification, a schema validation error is expected if `xsd:unique` is violated by using a compound key with an empty key.</span></span>  
  
## <a name="mitigation"></a><span data-ttu-id="aeda6-106">Limitation des risques</span><span class="sxs-lookup"><span data-stu-id="aeda6-106">Mitigation</span></span>  
 <span data-ttu-id="aeda6-107">Le fait qu'une erreur de validation de schéma soit détectée ou pas si une clé composée a une clé vide est une fonctionnalité que vous pouvez configurer :</span><span class="sxs-lookup"><span data-stu-id="aeda6-107">Whether a schema validation error is detected if a compound key has one empty key is a configurable feature:</span></span>  
  
- <span data-ttu-id="aeda6-108">Depuis les applications qui ciblent .NET Framework 4.6, la détection de l’erreur de validation de schéma est activée par défaut ; néanmoins, il est possible de la refuser afin que l’erreur de validation de schéma ne soit pas détectée.</span><span class="sxs-lookup"><span data-stu-id="aeda6-108">Starting with the apps that target the .NET Framework 4.6, detection of the schema validation error is enabled by default; however, it is possible to opt out of it, so that the schema validation error will not be detected.</span></span>  
  
- <span data-ttu-id="aeda6-109">Dans les applications qui s’exécutent sous .NET Framework 4.6, mais ciblent .NET Framework 4.5.2 et versions antérieures, la détection de l’erreur de validation de schéma n’est pas activée par défaut ; néanmoins, il est possible de l’activer afin que l’erreur de validation de schéma soit détectée.</span><span class="sxs-lookup"><span data-stu-id="aeda6-109">In apps that run under the .NET Framework 4.6 but target the .NET Framework 4.5.2 and earlier versions, a schema validation error is not detected by default; however, it is possible to opt into it, so that the schema validation error will be detected.</span></span>  
  
 <span data-ttu-id="aeda6-110">Ce comportement peut être configuré en utilisant la classe <xref:System.AppContext> pour définir la valeur du commutateur `System.Xml.IgnoreEmptyKeySequences`.</span><span class="sxs-lookup"><span data-stu-id="aeda6-110">This behavior can be configured by using the <xref:System.AppContext> class to define the value of the `System.Xml.IgnoreEmptyKeySequences` switch.</span></span> <span data-ttu-id="aeda6-111">Comme la valeur par défaut du commutateur est `false` (les séquences de touches vides ne sont pas ignorées), les applications qui ciblent .NET Framework 4.6 peuvent désactiver le comportement en utilisant le code suivant pour définir le commutateur avec la valeur `true` :</span><span class="sxs-lookup"><span data-stu-id="aeda6-111">Because the switch's default value is `false` (empty key sequences are not ignored), apps that target the .NET Framework 4.6 can opt out of the behavior by using the following code to set the switch's value to `true`:</span></span>  
  
 [!code-csharp[AppCompat.IgnoreEmptyKeySequences#1](../../../samples/snippets/csharp/VS_Snippets_CLR/appcompat.ignoreemptykeysequences/cs/program.cs#1)]
 [!code-vb[AppCompat.IgnoreEmptyKeySequences#1](../../../samples/snippets/visualbasic/VS_Snippets_CLR/appcompat.ignoreemptykeysequences/vb/module1.vb#1)]  
  
 <span data-ttu-id="aeda6-112">Pour les applications qui ciblent .NET Framework 4.5.2 et versions antérieures, comme la valeur par défaut du commutateur est `true` (les séquences de touches vides sont ignorées), il est possible de garantir qu’une clé composée avec une clé vide génère bel et bien une erreur de validation de schéma en utilisant le code suivant pour définir le commutateur avec la valeur `false`.</span><span class="sxs-lookup"><span data-stu-id="aeda6-112">For apps that target the .NET Framework 4.5.2 and earlier versions, because the switch's default value is `true` (empty key sequences are ignored), it is possible to ensure that a compound key with an empty key does generate a schema validation error by using the following code to set the switch's value to `false`.</span></span>  
  
 [!code-csharp[AppCompat.IgnoreEmptyKeySequences#2](../../../samples/snippets/csharp/VS_Snippets_CLR/appcompat.ignoreemptykeysequences/cs/program.cs#2)]
 [!code-vb[AppCompat.IgnoreEmptyKeySequences#2](../../../samples/snippets/visualbasic/VS_Snippets_CLR/appcompat.ignoreemptykeysequences/vb/module1.vb#2)]  
  
## <a name="see-also"></a><span data-ttu-id="aeda6-113">Voir aussi</span><span class="sxs-lookup"><span data-stu-id="aeda6-113">See also</span></span>

- [<span data-ttu-id="aeda6-114">Compatibilité des applications</span><span class="sxs-lookup"><span data-stu-id="aeda6-114">Application compatibility</span></span>](application-compatibility.md)
