---
title: 'Atténuation : validation du schéma XML'
ms.date: 03/30/2017
dev_langs:
- csharp
- vb
ms.assetid: b73dd4f4-f2dc-47a2-9425-3896e92321fb
author: rpetrusha
ms.author: ronpet
ms.openlocfilehash: fc0232e0187c795fe20e6a99d4a710ba6244e34e
ms.sourcegitcommit: 2701302a99cafbe0d86d53d540eb0fa7e9b46b36
ms.translationtype: HT
ms.contentlocale: fr-FR
ms.lasthandoff: 04/28/2019
ms.locfileid: "64599671"
---
# <a name="mitigation-xml-schema-validation"></a><span data-ttu-id="f258d-102">Atténuation : validation du schéma XML</span><span class="sxs-lookup"><span data-stu-id="f258d-102">Mitigation: XML Schema Validation</span></span>
<span data-ttu-id="f258d-103">Dans le [!INCLUDE[net_v46](../../../includes/net-v46-md.md)], la validation de schéma XSD détecte une violation de la contrainte unique si une clé composée est utilisée et qu'une clé est vide.</span><span class="sxs-lookup"><span data-stu-id="f258d-103">In the [!INCLUDE[net_v46](../../../includes/net-v46-md.md)], XSD schema validation detects a violation of the unique constraint if a compound key is used and one key is empty.</span></span>  
  
## <a name="impact"></a><span data-ttu-id="f258d-104">Impact</span><span class="sxs-lookup"><span data-stu-id="f258d-104">Impact</span></span>  
 <span data-ttu-id="f258d-105">L'impact de cette modification devrait être minime : selon la spécification de schéma, une erreur de validation de schéma est attendue si `xsd:unique` est enfreinte par l'utilisation d'une clé composée avec une clé vide.</span><span class="sxs-lookup"><span data-stu-id="f258d-105">The impact of this change should be minimal: based on the schema specification, a schema validation error is expected if `xsd:unique` is violated by using a compound key with an empty key.</span></span>  
  
## <a name="mitigation"></a><span data-ttu-id="f258d-106">Atténuation</span><span class="sxs-lookup"><span data-stu-id="f258d-106">Mitigation</span></span>  
 <span data-ttu-id="f258d-107">Le fait qu'une erreur de validation de schéma soit détectée ou pas si une clé composée a une clé vide est une fonctionnalité que vous pouvez configurer :</span><span class="sxs-lookup"><span data-stu-id="f258d-107">Whether a schema validation error is detected if a compound key has one empty key is a configurable feature:</span></span>  
  
- <span data-ttu-id="f258d-108">Depuis les applications qui ciblent le [!INCLUDE[net_v46](../../../includes/net-v46-md.md)], la détection de l'erreur de validation de schéma est activée par défaut ; néanmoins, il est possible de la refuser afin que l'erreur de validation de schéma ne soit pas détectée.</span><span class="sxs-lookup"><span data-stu-id="f258d-108">Starting with the apps that target the [!INCLUDE[net_v46](../../../includes/net-v46-md.md)], detection of the schema validation error is enabled by default; however, it is possible to opt out of it, so that the schema validation error will not be detected.</span></span>  
  
- <span data-ttu-id="f258d-109">Depuis les applications qui s'exécutent sous le [!INCLUDE[net_v46](../../../includes/net-v46-md.md)] mais ciblent le [!INCLUDE[net_v452](../../../includes/net-v452-md.md)] ou version antérieure, la détection de l'erreur de validation de schéma n'est pas activée par défaut ; néanmoins, il est possible de l'activer afin que l'erreur de validation de schéma soit détectée.</span><span class="sxs-lookup"><span data-stu-id="f258d-109">In apps that run under the [!INCLUDE[net_v46](../../../includes/net-v46-md.md)] but target the [!INCLUDE[net_v452](../../../includes/net-v452-md.md)] and earlier versions, a schema validation error is not detected by default; however, it is possible to opt into it, so that the schema validation error will be detected.</span></span>  
  
 <span data-ttu-id="f258d-110">Ce comportement peut être configuré en utilisant la classe <xref:System.AppContext> pour définir la valeur du commutateur `System.Xml.IgnoreEmptyKeySequences`.</span><span class="sxs-lookup"><span data-stu-id="f258d-110">This behavior can be configured by using the <xref:System.AppContext> class to define the value of the `System.Xml.IgnoreEmptyKeySequences` switch.</span></span> <span data-ttu-id="f258d-111">Comme la valeur du commutateur par défaut est `false` (les séquences de touches vides ne sont pas ignorées), les applications qui ciblent le [!INCLUDE[net_v46](../../../includes/net-v46-md.md)] peuvent désactiver le comportement en utilisant le code suivant pour définir le commutateur avec la valeur `true` :</span><span class="sxs-lookup"><span data-stu-id="f258d-111">Because the switch's default value is `false` (empty key sequences are not ignored), apps that target the [!INCLUDE[net_v46](../../../includes/net-v46-md.md)] can opt out of the behavior by using the following code to set the switch's value to `true`:</span></span>  
  
 [!code-csharp[AppCompat.IgnoreEmptyKeySequences#1](../../../samples/snippets/csharp/VS_Snippets_CLR/appcompat.ignoreemptykeysequences/cs/program.cs#1)]
 [!code-vb[AppCompat.IgnoreEmptyKeySequences#1](../../../samples/snippets/visualbasic/VS_Snippets_CLR/appcompat.ignoreemptykeysequences/vb/module1.vb#1)]  
  
 <span data-ttu-id="f258d-112">Pour les applications qui ciblent les versions [!INCLUDE[net_v452](../../../includes/net-v452-md.md)] et antérieures, comme la valeur du commutateur par défaut est `true` (les séquences de touches vides sont ignorées), il est possible de garantir qu'une clé composée avec une clé vide génère bel et bien une erreur de validation de schéma en utilisant le code suivant pour définir le commutateur avec la valeur `false`.</span><span class="sxs-lookup"><span data-stu-id="f258d-112">For apps that target the [!INCLUDE[net_v452](../../../includes/net-v452-md.md)] and earlier versions, because the switch's default value is `true` (empty key sequences are ignored), it is possible to ensure that a compound key with an empty key does generate a schema validation error by using the following code to set the switch's value to `false`.</span></span>  
  
 [!code-csharp[AppCompat.IgnoreEmptyKeySequences#2](../../../samples/snippets/csharp/VS_Snippets_CLR/appcompat.ignoreemptykeysequences/cs/program.cs#2)]
 [!code-vb[AppCompat.IgnoreEmptyKeySequences#2](../../../samples/snippets/visualbasic/VS_Snippets_CLR/appcompat.ignoreemptykeysequences/vb/module1.vb#2)]  
  
## <a name="see-also"></a><span data-ttu-id="f258d-113">Voir aussi</span><span class="sxs-lookup"><span data-stu-id="f258d-113">See also</span></span>

- [<span data-ttu-id="f258d-114">Modifications de reciblage</span><span class="sxs-lookup"><span data-stu-id="f258d-114">Retargeting Changes</span></span>](../../../docs/framework/migration-guide/retargeting-changes-in-the-net-framework-4-6.md)
