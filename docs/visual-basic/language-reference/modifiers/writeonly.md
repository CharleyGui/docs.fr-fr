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
ms.openlocfilehash: 847617ea6534089857a759fbea3bb16a3a5a36a1
ms.sourcegitcommit: 17ee6605e01ef32506f8fdc686954244ba6911de
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 11/22/2019
ms.locfileid: "74344188"
---
# <a name="writeonly-visual-basic"></a>WriteOnly (Visual Basic)
Spécifie qu’une propriété peut être écrite mais pas lue.  
  
## <a name="remarks"></a>Notes  
  
## <a name="rules"></a>Règles  
 **Contexte de déclaration.** Vous pouvez utiliser `WriteOnly` seulement au niveau du module. Cela signifie que le contexte de déclaration pour une propriété `WriteOnly` doit être une classe, une structure ou un module, et ne peut pas être un fichier source, un espace de noms ou une procédure.  
  
 Vous pouvez déclarer une propriété en tant que `WriteOnly`, mais pas une variable.  
  
## <a name="when-to-use-writeonly"></a>Quand utiliser WriteOnly  
 Parfois, vous souhaitez que le code de consommation soit en mesure de définir une valeur, mais pas de le découvrir. Par exemple, les données sensibles, telles qu’un numéro d’enregistrement social ou un mot de passe, doivent être protégées contre tout composant qui n’a pas été défini. Dans ce cas, vous pouvez utiliser une propriété `WriteOnly` pour définir la valeur.  
  
> [!IMPORTANT]
> Lorsque vous définissez et utilisez une propriété `WriteOnly`, tenez compte des mesures de protection supplémentaires suivantes :  
  
- **Substitution.** Si la propriété est membre d’une classe, autorisez-la comme valeur par défaut [NotOverridable](../../../visual-basic/language-reference/modifiers/notoverridable.md)et ne la déclarez pas `Overridable` ou `MustOverride`. Cela empêche une classe dérivée d’accéder à un accès indésirable par le biais d’une substitution.  
  
- **Niveau d’accès.** Si vous conservez les données sensibles de la propriété dans une ou plusieurs variables, déclarez-les comme [privées](../../../visual-basic/language-reference/modifiers/private.md) afin qu’aucun autre code ne puisse y accéder.  
  
- **Chiffre.** Stockez toutes les données sensibles au format chiffré plutôt qu’en texte brut. Si du code malveillant parvient à accéder à cette zone de mémoire, il est plus difficile d’utiliser les données. Le chiffrement est également utile s’il est nécessaire de sérialiser les données sensibles.  
  
- **La réinitialisation.** Lorsque la classe, la structure ou le module définissant la propriété est terminé, réinitialisez les données sensibles aux valeurs par défaut ou à d’autres valeurs non significatives. Cela offre une protection supplémentaire lorsque cette zone de mémoire est libérée pour un accès général.  
  
- **Persistance.** Ne conservez pas les données sensibles, par exemple sur le disque, si vous pouvez les éviter. En outre, n’écrivez pas de données sensibles dans le presse-papiers.  
  
 Le modificateur `WriteOnly` peut être utilisé dans ce contexte :  
  
 [Property (instruction)](../../../visual-basic/language-reference/statements/property-statement.md)  
  
## <a name="see-also"></a>Voir aussi

- [ReadOnly](../../../visual-basic/language-reference/modifiers/readonly.md)
- [Private](../../../visual-basic/language-reference/modifiers/private.md)
- [Mots clés](../../../visual-basic/language-reference/keywords/index.md)
