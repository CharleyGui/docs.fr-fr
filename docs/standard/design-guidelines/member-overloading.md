---
title: Surcharge de membre
ms.date: 10/22/2008
helpviewer_keywords:
- default arguments
- members [.NET Framework], overloaded
- member design guidelines [.NET Framework], overloading
- overloaded members
- signatures, members
ms.assetid: 964ba19e-8b94-4b5b-b1e3-5a0b531a0bb1
ms.openlocfilehash: fe8bf23a04e6684564d3d7e287c2a009e0817732
ms.sourcegitcommit: d8020797a6657d0fbbdff362b80300815f682f94
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 11/24/2020
ms.locfileid: "95706630"
---
# <a name="member-overloading"></a>Surcharge de membre

La surcharge de membre consiste à créer deux membres ou plus sur le même type qui diffèrent uniquement par le nombre ou le type de paramètres, mais qui portent le même nom. Par exemple, dans le code suivant, la `WriteLine` méthode est surchargée :

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

 ✔️ essayez d’utiliser des noms de paramètres descriptifs pour indiquer la valeur par défaut utilisée par les surcharges plus courtes.

 ❌ Évitez la variation arbitraire des noms de paramètres dans les surcharges. Si un paramètre d’une surcharge représente la même entrée qu’un paramètre dans une autre surcharge, les paramètres doivent avoir le même nom.

 ❌ Évitez d’être incohérent dans l’ordre des paramètres dans les membres surchargés. Les paramètres portant le même nom doivent apparaître à la même position dans toutes les surcharges.

 ✔️ Effectuez uniquement la surcharge virtuelle la plus longue (si l’extensibilité est requise). Les surcharges plus courtes doivent simplement appeler une surcharge plus longue.

 ❌ N’utilisez pas `ref` `out` les modificateurs ou pour surcharger des membres.

 Certains langages ne peuvent pas résoudre les appels aux surcharges de ce type. En outre, ces surcharges ont généralement une sémantique complètement différente et ne doivent probablement pas être des surcharges, mais deux méthodes distinctes à la place.

 ❌ N’ont pas de surcharges avec des paramètres à la même position et des types similaires encore avec une sémantique différente.

 ✔️ autoriser `null` à être passé pour des arguments facultatifs.

 ✔️ Utilisez la surcharge des membres plutôt que de définir des membres avec des arguments par défaut.

 Les arguments par défaut ne sont pas conformes CLS.

 *Parties © 2005, 2009 Microsoft Corporation. Tous droits réservés.*

 *Réimprimé avec l’autorisation de Pearson Education, Inc. et extrait de [Framework Design Guidelines: Conventions, Idioms, and Patterns for Reusable .NET Libraries, 2nd Edition](https://www.informit.com/store/framework-design-guidelines-conventions-idioms-and-9780321545619) par Krzysztof Cwalina et Brad Abrams, publié le 22 octobre 2008 par Addison-Wesley Professional dans le cadre de la série sur le développement Microsoft Windows.*

## <a name="see-also"></a>Voir aussi

- [Recommandations en matière de conception de membres](member.md)
- [Directives de conception d’infrastructure](index.md)
