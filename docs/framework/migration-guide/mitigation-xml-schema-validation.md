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
# <a name="mitigation-xml-schema-validation"></a>Atténuation : validation du schéma XML
Dans .NET Framework 4.6, la validation de schéma XSD détecte une violation de contrainte unique si une clé composée est utilisée et qu’une clé est vide.  
  
## <a name="impact"></a>Impact  
 L'impact de cette modification devrait être minime : selon la spécification de schéma, une erreur de validation de schéma est attendue si `xsd:unique` est enfreinte par l'utilisation d'une clé composée avec une clé vide.  
  
## <a name="mitigation"></a>Atténuation  
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

- [Modifications de reciblage](../../../docs/framework/migration-guide/retargeting-changes-in-the-net-framework-4-6.md)
