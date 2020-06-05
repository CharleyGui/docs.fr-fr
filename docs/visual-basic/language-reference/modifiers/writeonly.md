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
# <a name="writeonly-visual-basic"></a>WriteOnly (Visual Basic)
Spécifie qu’une propriété peut être écrite mais pas lue.  
  
## <a name="remarks"></a>Notes  
  
## <a name="rules"></a>Règles  
 **Contexte de déclaration.** Vous pouvez utiliser `WriteOnly` seulement au niveau du module. Cela signifie que le contexte de déclaration pour une `WriteOnly` propriété doit être une classe, une structure ou un module, et ne peut pas être un fichier source, un espace de noms ou une procédure.  
  
 Vous pouvez déclarer une propriété en tant que `WriteOnly` , mais pas en tant que variable.  
  
## <a name="when-to-use-writeonly"></a>Quand utiliser WriteOnly  
 Parfois, vous souhaitez que le code de consommation soit en mesure de définir une valeur, mais pas de le découvrir. Par exemple, les données sensibles, telles qu’un numéro d’enregistrement social ou un mot de passe, doivent être protégées contre tout composant qui n’a pas été défini. Dans ce cas, vous pouvez utiliser une `WriteOnly` propriété pour définir la valeur.  
  
> [!IMPORTANT]
> Lorsque vous définissez et utilisez une `WriteOnly` propriété, tenez compte des mesures de protection supplémentaires suivantes :  
  
- **Substitution.** Si la propriété est membre d’une classe, autorisez-la comme valeur par défaut [NotOverridable](notoverridable.md)et ne la déclarez pas `Overridable` ou `MustOverride` . Cela empêche une classe dérivée d’accéder à un accès indésirable par le biais d’une substitution.  
  
- **Niveau d’accès.** Si vous conservez les données sensibles de la propriété dans une ou plusieurs variables, déclarez-les comme [privées](private.md) afin qu’aucun autre code ne puisse y accéder.  
  
- **Chiffre.** Stockez toutes les données sensibles au format chiffré plutôt qu’en texte brut. Si du code malveillant parvient à accéder à cette zone de mémoire, il est plus difficile d’utiliser les données. Le chiffrement est également utile s’il est nécessaire de sérialiser les données sensibles.  
  
- **La réinitialisation.** Lorsque la classe, la structure ou le module définissant la propriété est terminé, réinitialisez les données sensibles aux valeurs par défaut ou à d’autres valeurs non significatives. Cela offre une protection supplémentaire lorsque cette zone de mémoire est libérée pour un accès général.  
  
- **Persistance.** Ne conservez pas les données sensibles, par exemple sur le disque, si vous pouvez les éviter. En outre, n’écrivez pas de données sensibles dans le presse-papiers.  
  
 Le `WriteOnly` modificateur peut être utilisé dans ce contexte :  
  
 [Property Statement](../statements/property-statement.md)  
  
## <a name="see-also"></a>Voir aussi

- [Seulement](readonly.md)
- [Privé](private.md)
- [Mots clés](../keywords/index.md)
