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
# <a name="mitigation-xml-schema-validation"></a>Atténuation : Validation du schéma XML
Dans .NET Framework 4.6, la validation de schéma XSD détecte une violation de contrainte unique si une clé composée est utilisée et qu’une clé est vide.  
  
## <a name="impact"></a>Impact  
 L'impact de cette modification devrait être minime : selon la spécification de schéma, une erreur de validation de schéma est attendue si `xsd:unique` est enfreinte par l'utilisation d'une clé composée avec une clé vide.  
  
## <a name="mitigation"></a>Limitation des risques  
 Le fait qu'une erreur de validation de schéma soit détectée ou pas si une clé composée a une clé vide est une fonctionnalité que vous pouvez configurer :  
  
- Depuis les applications qui ciblent .NET Framework 4.6, la détection de l’erreur de validation de schéma est activée par défaut ; néanmoins, il est possible de la refuser afin que l’erreur de validation de schéma ne soit pas détectée.  
  
- Dans les applications qui s’exécutent sous .NET Framework 4.6, mais ciblent .NET Framework 4.5.2 et versions antérieures, la détection de l’erreur de validation de schéma n’est pas activée par défaut ; néanmoins, il est possible de l’activer afin que l’erreur de validation de schéma soit détectée.  
  
 Ce comportement peut être configuré en utilisant la classe <xref:System.AppContext> pour définir la valeur du commutateur `System.Xml.IgnoreEmptyKeySequences`. Comme la valeur par défaut du commutateur est `false` (les séquences de touches vides ne sont pas ignorées), les applications qui ciblent .NET Framework 4.6 peuvent désactiver le comportement en utilisant le code suivant pour définir le commutateur avec la valeur `true` :  
  
 [!code-csharp[AppCompat.IgnoreEmptyKeySequences#1](../../../samples/snippets/csharp/VS_Snippets_CLR/appcompat.ignoreemptykeysequences/cs/program.cs#1)]
 [!code-vb[AppCompat.IgnoreEmptyKeySequences#1](../../../samples/snippets/visualbasic/VS_Snippets_CLR/appcompat.ignoreemptykeysequences/vb/module1.vb#1)]  
  
 Pour les applications qui ciblent .NET Framework 4.5.2 et versions antérieures, comme la valeur par défaut du commutateur est `true` (les séquences de touches vides sont ignorées), il est possible de garantir qu’une clé composée avec une clé vide génère bel et bien une erreur de validation de schéma en utilisant le code suivant pour définir le commutateur avec la valeur `false`.  
  
 [!code-csharp[AppCompat.IgnoreEmptyKeySequences#2](../../../samples/snippets/csharp/VS_Snippets_CLR/appcompat.ignoreemptykeysequences/cs/program.cs#2)]
 [!code-vb[AppCompat.IgnoreEmptyKeySequences#2](../../../samples/snippets/visualbasic/VS_Snippets_CLR/appcompat.ignoreemptykeysequences/vb/module1.vb#2)]  
  
## <a name="see-also"></a>Voir aussi

- [Compatibilité des applications](application-compatibility.md)
