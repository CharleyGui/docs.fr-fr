---
title: WriteOnly (Visual Basic)
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
ms.openlocfilehash: 163ec17f3ea96744290c54a73054ab132f842127
ms.sourcegitcommit: 2701302a99cafbe0d86d53d540eb0fa7e9b46b36
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 04/28/2019
ms.locfileid: "64647647"
---
# <a name="writeonly-visual-basic"></a>WriteOnly (Visual Basic)
Spécifie qu’une propriété peut être écrite, mais pas lire.  
  
## <a name="remarks"></a>Notes  
  
## <a name="rules"></a>Règles  
 **Contexte de déclaration.** Vous pouvez utiliser `WriteOnly` seulement au niveau du module. Cela signifie que le contexte de déclaration pour un `WriteOnly` propriété doit être une classe, une structure ou un module et ne peut pas être un fichier source, un espace de noms ou une procédure.  
  
 Vous pouvez déclarer une propriété en tant que `WriteOnly`, mais pas une variable.  
  
## <a name="when-to-use-writeonly"></a>Quand utiliser WriteOnly  
 Parfois, vous souhaitez le code pour pouvoir définir une valeur mais pas découvrir ce qu’il est utilisé. Par exemple, des données sensibles, comme un numéro d’enregistrement de réseaux sociaux ou un mot de passe doivent être protégé contre tout accès par tout composant qui définissait pas. Dans ce cas, vous pouvez utiliser un `WriteOnly` propriété pour définir la valeur.  
  
> [!IMPORTANT]
>  Lorsque vous définissez et utilisez un `WriteOnly` propriété, envisagez les mesures de protection supplémentaires suivantes :  
  
- **À substituer.** Si la propriété est un membre d’une classe, laissez-le par défaut [NotOverridable](../../../visual-basic/language-reference/modifiers/notoverridable.md)et ne la déclarez pas `Overridable` ou `MustOverride`. Cela empêche une classe dérivée d’apporter un droit d’accès via un remplacement.  
  
- **Niveau d’accès.** Si vous stockez des données sensibles de la propriété dans une ou plusieurs variables, déclarez-les [privée](../../../visual-basic/language-reference/modifiers/private.md) afin qu’aucun autre code pour n’y accéder.  
  
- **Chiffrement.** Store toutes les données sensibles sous forme chiffrée plutôt qu’en texte brut. Si un code malveillant d’une certaine manière parvient à accéder à cette zone de mémoire, il est plus difficile d’utiliser des données. Le chiffrement est également utile s’il est nécessaire de sérialiser les données sensibles.  
  
- **La réinitialisation.** Lors de la classe, une structure ou un module définissant la propriété est terminée, réinitialisez les données sensibles aux valeurs par défaut ou avec d’autres valeurs sans signification. Cela offre une protection supplémentaire lorsque cette zone de mémoire est libérée pour l’accès général.  
  
- **Persistance.** Ne sont pas conservés toutes les données sensibles, par exemple sur le disque, si vous pouvez l’éviter. En outre, n’écrivez pas toutes les données sensibles dans le Presse-papiers.  
  
 Le `WriteOnly` modificateur peut être utilisé dans ce contexte :  
  
 [Property (instruction)](../../../visual-basic/language-reference/statements/property-statement.md)  
  
## <a name="see-also"></a>Voir aussi

- [ReadOnly](../../../visual-basic/language-reference/modifiers/readonly.md)
- [Private](../../../visual-basic/language-reference/modifiers/private.md)
- [Mots clés](../../../visual-basic/language-reference/keywords/index.md)
