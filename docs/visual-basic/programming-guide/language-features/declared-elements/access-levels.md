---
title: Niveaux d'accès dans Visual Basic
ms.date: 05/10/2018
helpviewer_keywords:
- members [Visual Basic], accessing in Visual Basic
- Friend access modifier
- access levels, declared elements
- access levels
- access modifiers
- Public access modifier
- Protected access modifier
- Protected Friend access modifier
- Private Protected access modifier
- Private access modifier
- declared elements [Visual Basic], access level
ms.assetid: 6e06c1ab-fd78-47f0-83a8-1152780b5e1a
ms.openlocfilehash: d1548f7850c68bc3c5422cf9d8d3d30eaa4aa8f3
ms.sourcegitcommit: ad800f019ac976cb669e635fb0ea49db740e6890
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 10/29/2019
ms.locfileid: "73035882"
---
# <a name="access-levels-in-visual-basic"></a>Niveaux d'accès dans Visual Basic

Le *niveau d’accès* d’un élément déclaré est l’étendue de la capacité à y accéder, c’est-à-dire le code qui a l’autorisation de le lire ou d’y écrire. Cela est déterminé non seulement par la manière dont vous déclarez l’élément lui-même, mais également par le niveau d’accès du conteneur de l’élément. Le code qui ne peut pas accéder à un élément conteneur ne peut accéder à aucun de ses éléments contenus, même ceux qui sont déclarés comme `Public`. Par exemple, il est possible d’accéder à une variable `Public` dans une structure `Private` à l’intérieur de la classe qui contient la structure, mais pas à l’extérieur de cette classe.

## <a name="public"></a>Public

Le mot clé [public](../../../language-reference/modifiers/public.md) dans l’instruction de déclaration spécifie que l’élément est accessible à partir du code n’importe où dans le même projet, à partir d’autres projets qui référencent le projet et à partir de n’importe quel assembly généré à partir du projet. Le code suivant illustre un exemple de déclaration de `Public` :

```vb
Public Class ClassForEverybody
```

Vous pouvez utiliser `Public` uniquement au niveau du module, de l’interface ou de l’espace de noms. Cela signifie que vous pouvez déclarer un élément public au niveau d’un fichier source ou d’un espace de noms, ou à l’intérieur d’une interface, d’un module, d’une classe ou d’une structure, mais pas dans une procédure.
  
## <a name="protected"></a>Protected

Le mot clé [protected](../../../language-reference/modifiers/protected.md) dans l’instruction de déclaration spécifie que l’élément est accessible uniquement à partir de la même classe ou d’une classe dérivée de cette classe. Le code suivant illustre un exemple de déclaration de `Protected` :

```vb
Protected Class ClassForMyHeirs
```

Vous pouvez utiliser `Protected` uniquement au niveau de la classe et uniquement lorsque vous déclarez un membre d’une classe. Cela signifie que vous pouvez déclarer un élément protégé dans une classe, mais pas au niveau d’un fichier ou d’un espace de noms source, ou à l’intérieur d’une interface, d’un module, d’une structure ou d’une procédure.

## <a name="friend"></a>Friend

Le mot clé [Friend](../../../language-reference/modifiers/friend.md) dans l’instruction de déclaration spécifie que l’élément est accessible à partir du même assembly, mais pas à l’extérieur de l’assembly. Le code suivant illustre un exemple de déclaration de `Friend` :

```vb
Friend stringForThisProject As String
```

Vous pouvez utiliser `Friend` uniquement au niveau du module, de l’interface ou de l’espace de noms. Cela signifie que vous pouvez déclarer un élément Friend au niveau d’un fichier source ou d’un espace de noms, ou à l’intérieur d’une interface, d’un module, d’une classe ou d’une structure, mais pas dans une procédure.

## <a name="protected-friend"></a>Protected Friend

La combinaison de mots clés [Protected Friend](../../../language-reference/modifiers/protected-friend.md) dans l’instruction de déclaration spécifie que l’élément est accessible soit à partir de classes dérivées, soit à partir d’un même assembly, ou les deux. Le code suivant illustre un exemple de déclaration de `Protected Friend` :

```vb
Protected Friend stringForProjectAndHeirs As String
```

Vous pouvez utiliser `Protected Friend` uniquement au niveau de la classe et uniquement lorsque vous déclarez un membre d’une classe. Cela signifie que vous pouvez déclarer un élément Friend protégé dans une classe, mais pas au niveau d’un fichier ou d’un espace de noms source, ou à l’intérieur d’une interface, d’un module, d’une structure ou d’une procédure.

## <a name="private"></a>Private

Le mot clé [Private](../../../language-reference/modifiers/private.md) dans l’instruction de déclaration spécifie que l’élément est accessible uniquement à partir du même module, de la même classe ou de la même structure. Le code suivant illustre un exemple de déclaration de `Private` :

```vb
Private _numberForMeOnly As Integer
```

Vous pouvez utiliser `Private` seulement au niveau du module. Cela signifie que vous pouvez déclarer un élément privé à l’intérieur d’un module, d’une classe ou d’une structure, mais pas au niveau d’un fichier ou d’un espace de noms source, à l’intérieur d’une interface ou dans une procédure.

Au niveau du module, l’instruction `Dim` sans mot clé de niveau d’accès équivaut à une déclaration de `Private`. Toutefois, vous souhaiterez peut-être utiliser le mot clé `Private` pour faciliter la lecture et l’interprétation de votre code.

## <a name="private-protected"></a>Private Protected

La combinaison de mots clés [protégés privés](../../../language-reference/modifiers/private-protected.md) dans l’instruction de déclaration spécifie que l’élément est accessible uniquement à partir de la même classe, ainsi qu’à partir de classes dérivées qui se trouvent dans le même assembly que la classe conteneur. Le modificateur d’accès `Private Protected` est pris en charge à partir de Visual Basic 15,5.

L’exemple suivant illustre une déclaration de `Private Protected` :

```vb
Private Protected internalValue As Integer
```

Vous pouvez déclarer un élément `Private Protected` uniquement à l’intérieur d’une classe. Vous ne pouvez pas le déclarer dans une interface ou une structure, ni le déclarer au niveau d’un fichier ou d’un espace de noms source, à l’intérieur d’une interface ou d’une structure, ou dans une procédure.

Le modificateur d’accès `Private Protected` est pris en charge par Visual Basic 15,5 et versions ultérieures. Pour l’utiliser, vous ajoutez l’élément suivant à votre fichier de projet de Visual Basic ( *\*. vbproj*). Tant que Visual Basic 15,5 ou version ultérieure est installé sur votre système, il vous permet de tirer parti de toutes les fonctionnalités de langage prises en charge par la dernière version du compilateur Visual Basic :

```xml
<PropertyGroup>
   <LangVersion>latest</LangVersion>
</PropertyGroup>
```

Pour utiliser le modificateur d’accès `Private Protected`, vous devez ajouter l’élément suivant à votre fichier projet Visual Basic ( *\*. vbproj*) :

```xml
<PropertyGroup>
   <LangVersion>15.5</LangVersion>
</PropertyGroup>
```

Pour plus d’informations, consultez [définition de la version du langage Visual Basic](../../../language-reference/configure-language-version.md).

## <a name="access-modifiers"></a>Modificateurs d’accès

Les mots clés qui spécifient le niveau d’accès sont appelés *modificateurs d’accès*. Le tableau suivant compare les modificateurs d’accès :

|Modificateur d’accès|Niveau d’accès accordé|Éléments que vous pouvez déclarer avec ce niveau d’accès|Contexte de déclaration dans lequel vous pouvez utiliser ce modificateur|
|---------------------|--------------------------|-----------------------------------------------------|----------------------------------------------------------------|
|`Public`|Illimité<br /><br /> Tout code pouvant voir un élément public peut y accéder|Interfaces<br /><br /> Modules<br /><br /> Classes<br /><br /> Structures<br /><br /> Membres de structure<br /><br /> Procédures<br /><br /> Propriétés<br /><br /> Variables membres<br /><br /> Constantes<br /><br /> Énumérations<br /><br /> événements<br /><br /> Déclarations externes<br /><br /> Délégués|Fichier source<br /><br /> Espace de noms<br /><br /> Interface<br /><br /> Module<br /><br /> Class<br /><br /> Structure|
|`Protected`|Dérivation :<br /><br /> Le code de la classe qui déclare un élément protégé, ou une classe dérivée de celui-ci, peut accéder à l’élément|Interfaces<br /><br /> Classes<br /><br /> Structures<br /><br /> Procédures<br /><br /> Propriétés<br /><br /> Variables membres<br /><br /> Constantes<br /><br /> Énumérations<br /><br /> événements<br /><br /> Déclarations externes<br /><br /> Délégués|Class|
|`Friend`|Assembly :<br /><br /> Le code de l’assembly qui déclare un élément Friend peut y accéder|Interfaces<br /><br /> Modules<br /><br /> Classes<br /><br /> Structures<br /><br /> Membres de structure<br /><br /> Procédures<br /><br /> Propriétés<br /><br /> Variables membres<br /><br /> Constantes<br /><br /> Énumérations<br /><br /> événements<br /><br /> Déclarations externes<br /><br /> Délégués|Fichier source<br /><br /> Espace de noms<br /><br /> Interface<br /><br /> Module<br /><br /> Class<br /><br /> Structure|
|`Protected` `Friend`|Union de `Protected` et `Friend`:<br /><br /> Du code dans la même classe ou dans le même assembly qu’un élément Friend protégé, ou dans toute classe dérivée de la classe de l’élément, peut y accéder|Interfaces<br /><br /> Classes<br /><br /> Structures<br /><br /> Procédures<br /><br /> Propriétés<br /><br /> Variables membres<br /><br /> Constantes<br /><br /> Énumérations<br /><br /> événements<br /><br /> Déclarations externes<br /><br /> Délégués|Class|
|`Private`|Contexte de déclaration :<br /><br /> Le code du type qui déclare un élément privé, y compris le code dans les types contenus, peut accéder à l’élément|Interfaces<br /><br /> Classes<br /><br /> Structures<br /><br /> Membres de structure<br /><br /> Procédures<br /><br /> Propriétés<br /><br /> Variables membres<br /><br /> Constantes<br /><br /> Énumérations<br /><br /> événements<br /><br /> Déclarations externes<br /><br /> Délégués|Module<br /><br /> Class<br /><br /> Structure|
|`Private Protected`|Code dans la classe qui déclare un élément protégé privé, ou code dans une classe dérivée trouvée dans le même assembly que la classe bas.|Interfaces<br /><br /> Classes<br /><br /> Structures<br /><br /> Procédures<br /><br /> Propriétés<br /><br /> Variables membres<br /><br /> Constantes<br /><br /> Énumérations<br /><br /> événements<br /><br /> Déclarations externes<br /><br /> Délégués|Class|

## <a name="see-also"></a>Voir aussi

- [Dim (instruction)](../../../language-reference/statements/dim-statement.md)
- [Static](../../../language-reference/modifiers/static.md)
- [Noms d’éléments déclarés](declared-element-names.md)
- [Références aux éléments déclarés](references-to-declared-elements.md)
- [Caractéristiques d’éléments déclarés](declared-element-characteristics.md)
- [Durée de vie dans Visual Basic](lifetime.md)
- [Étendue dans Visual Basic](scope.md)
- [Guide pratique : contrôler la disponibilité d’une variable](how-to-control-the-availability-of-a-variable.md)
- [Variables](../variables/index.md)
- [Déclaration de variable](../variables/variable-declaration.md)
