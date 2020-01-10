---
title: Surcharge de membre
ms.date: 10/22/2008
ms.technology: dotnet-standard
helpviewer_keywords:
- default arguments
- members [.NET Framework], overloaded
- member design guidelines [.NET Framework], overloading
- overloaded members
- signatures, members
ms.assetid: 964ba19e-8b94-4b5b-b1e3-5a0b531a0bb1
ms.openlocfilehash: e7decab042dd1ee36beacb18956e175196cd112c
ms.sourcegitcommit: 5f236cd78cf09593c8945a7d753e0850e96a0b80
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 01/07/2020
ms.locfileid: "75709281"
---
# <a name="member-overloading"></a>Surcharge de membre
La surcharge de membre consiste à créer deux membres ou plus sur le même type qui diffèrent uniquement par le nombre ou le type de paramètres, mais qui portent le même nom. Par exemple, dans le code suivant, la méthode `WriteLine` est surchargée :  
  
```csharp  
public static class Console {  
    public void WriteLine();  
    public void WriteLine(string value);  
    public void WriteLine(bool value);  
    ...  
}  
```  
  
 Étant donné que seules les méthodes, les constructeurs et les propriétés indexées peuvent avoir des paramètres, seuls ces membres peuvent être surchargés.  
  
 La surcharge est l’une des techniques les plus importantes pour améliorer la convivialité, la productivité et la lisibilité des bibliothèques réutilisables. La surcharge sur le nombre de paramètres permet de fournir des versions plus simples des constructeurs et des méthodes. La surcharge sur le type de paramètre permet d’utiliser le même nom de membre pour les membres effectuant des opérations identiques sur un ensemble sélectionné de types différents.  
  
 **✓ DO** essayez d’utiliser des noms de paramètres descriptifs pour indiquer la valeur par défaut utilisée par les surcharges plus courts.  
  
 **X AVOID** Variant de façon arbitraire les noms de paramètres dans les surcharges. Si un paramètre d’une surcharge représente la même entrée qu’un paramètre dans une autre surcharge, les paramètres doivent avoir le même nom.  
  
 **X AVOID** incohérent dans l’ordre des paramètres de surcharge membres. Les paramètres portant le même nom doivent apparaître à la même position dans toutes les surcharges.  
  
 **✓ DO** créer uniquement la surcharge la plus longue virtuelle (si l’extensibilité est requise). Les surcharges plus courtes doivent simplement appeler une surcharge plus longue.  
  
 **X DO NOT** utiliser `ref` ou `out` modificateurs pour surcharger les membres.  
  
 Certains langages ne peuvent pas résoudre les appels aux surcharges de ce type. En outre, ces surcharges ont généralement une sémantique complètement différente et ne doivent probablement pas être des surcharges, mais deux méthodes distinctes à la place.  
  
 **X DO NOT** ont des surcharges avec des paramètres à la même position et les types semblables, mais avec une sémantique différente.  
  
 **✓ DO** autoriser `null` à passer les arguments facultatifs.  
  
 **✓ DO** utiliser membre surcharge plutôt que de définir des membres avec des arguments par défaut.  
  
 Les arguments par défaut ne sont pas conformes CLS.  
  
 *Parties © 2005, 2009 Microsoft Corporation. Tous droits réservés.*  
  
 *Réimprimé avec l’autorisation de Pearson Education, Inc. et extrait de [Framework Design Guidelines: Conventions, Idioms, and Patterns for Reusable .NET Libraries, 2nd Edition](https://www.informit.com/store/framework-design-guidelines-conventions-idioms-and-9780321545619) par Krzysztof Cwalina et Brad Abrams, publié le 22 octobre 2008 par Addison-Wesley Professional dans le cadre de la série sur le développement Microsoft Windows.*  
  
## <a name="see-also"></a>Voir aussi

- [Instructions de conception des membres](../../../docs/standard/design-guidelines/member.md)
- [Règles de conception de .NET Framework](../../../docs/standard/design-guidelines/index.md)
