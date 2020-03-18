---
title: Traitement du fichier XML - Guide de programmation C
ms.date: 07/20/2015
helpviewer_keywords:
- XML processing [C#]
- XML [C#], processing
ms.assetid: 60c71193-9dac-4cd3-98c5-100bd0edcc42
ms.openlocfilehash: bc72cade9ce6edddb88d741a3424405bba0a7ad8
ms.sourcegitcommit: 7588136e355e10cbc2582f389c90c127363c02a5
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 03/14/2020
ms.locfileid: "76793389"
---
# <a name="processing-the-xml-file-c-programming-guide"></a>Traitement du fichier XML (guide de programmation C)

Le compilateur génère une chaîne d’ID pour chaque construction de votre code qui est marquée pour générer la documentation. (Pour plus d’informations sur la façon d’étiqueter votre code, voir [les balises recommandées pour les commentaires de documentation](./recommended-tags-for-documentation-comments.md).) La chaîne ID identifie de façon unique la construction. Les programmes qui traitent le fichier XML peuvent utiliser la chaîne d’identification pour identifier l’élément de métadonnées/réflexion .NET Framework correspondant auquel s’applique la documentation.

Le fichier XML n’est pas une représentation hiérarchique de votre code. Il s’agit d’une liste plate avec un ID généré pour chaque élément.

Le compilateur respecte les règles suivantes quand il génère les chaînes d’ID :

- La chaîne ne contient aucun espace blanc.

- La première partie de la chaîne d’ID identifie le genre de membre identifié, au moyen d’un caractère unique suivi de deux-points. Les types de membres suivants sont utilisés :

    |Caractère|Description|
    |---------------|-----------------|
    |N|espace de noms<br /><br /> Vous ne pouvez pas ajouter de commentaires de documentation à un espace de noms, mais vous pouvez faire des références cref à des commentaires, si cela est pris en charge.|
    |T|type : classe, interface, struct, enum ou délégué|
    |F|field|
    |P|propriété (notamment des indexeurs ou autres propriétés indexées)|
    |M|méthode (notamment des méthodes spéciales telles que des constructeurs, des opérateurs, etc.)|
    |E|événement|
    |!|chaîne d’erreur<br /><br /> Le reste de la chaîne fournit des informations sur l’erreur. Le compilateur C# génère des informations d’erreur pour les liens qui ne peuvent pas être résolus.|

- La deuxième partie de la chaîne est le nom qualifié complet de l’élément, en commençant à la racine de l’espace de noms. Le nom de l’élément, ses types englobants et l’espace de noms sont séparés par des points. Si le nom de l’élément lui-même comporte des points, ceux-ci sont remplacés par un signe dièse (« # »). Il est supposé qu’aucun élément n’a un signe dièse directement dans son nom. Par exemple, le nom qualifié complet du constructeur String serait « System.String.#ctor ».

- Pour les propriétés et méthodes, si la méthode a des arguments, la liste d’arguments entre parenthèses suit. S’il n’y a pas d’arguments, aucune parenthèse n’est présente. Les arguments sont séparés par des virgules. L’encodage de chaque argument correspond directement à son encodage dans une signature .NET Framework :

  - Types de base. Les types réguliers (ELEMENT_TYPE_CLASS ou ELEMENT_TYPE_VALUETYPE) sont représentés en tant que nom qualifié complet du type.

  - Les types intrinsèques (par exemple, ELEMENT_TYPE_I4, ELEMENT_TYPE_OBJECT, ELEMENT_TYPE_STRING, ELEMENT_TYPE_TYPEDBYREF et ELEMENT_TYPE_VOID) sont représentés comme le nom entièrement qualifié du type complet correspondant. Par exemple, System.Int32 ou System.TypedReference.

  - ELEMENT_TYPE_PTR est représenté par un « \* » après le type modifié.

  - ELEMENT_TYPE_BYREF est représenté par un '\@' après le type modifié.

  - ELEMENT_TYPE_PINNED est représenté par un « ^ » après le type modifié. Le compilateur C# ne génère jamais ceci.

  - ELEMENT_TYPE_CMOD_REQ est représenté par un « &#124; » et le nom qualifié complet de la classe de modification, après le type modifié. Le compilateur C# ne génère jamais ceci.

  - ELEMENT_TYPE_CMOD_OPT est représenté par un « ! » et le nom qualifié complet de la classe de modification, après le type modifié.

  - ELEMENT_TYPE_SZARRAY est représenté par « [] » après le type d’élément du tableau.

  - ELEMENT_TYPE_GENERICARRAY est représenté par « [?] » après le type d’élément du tableau. Le compilateur C# ne génère jamais ceci.

  - ELEMENT_TYPE_ARRAY est représenté comme *[en*`size`baisse :`size`, plus*bas*: ] où le nombre de virgules est le rang - 1, et les limites inférieures et la taille de chaque dimension, si elles sont connues, sont représentées en décimale. Si la limite inférieure ou la taille n’est pas spécifiée, elle est simplement omise. Si la limite inférieure et la taille d’une dimension particulière sont omises, le « : » est également omis. Par exemple, un tableau à deux dimensions avec 1 comme limite inférieure et une taille non spécifiée est [1:,1:].

  - ELEMENT_TYPE_FNPTR est représenté en tant que « =FUNC:`type`(*signature*) », où `type` est le type de retour et *signature* correspond aux arguments de la méthode. S’il n’y a pas d’argument, les parenthèses sont omises. Le compilateur C# ne génère jamais ceci.

    Les composants de signature suivants ne sont pas représentés, car ils ne sont jamais utilisés pour différencier les méthodes surchargées :

  - convention d’appel

  - type de retour

  - ELEMENT_TYPE_SENTINEL

- Pour les opérateurs de conversion uniquement (op_Implicit et op_Explicit), la valeur de retour de la méthode est encodée en tant que « ~ » suivi du type de retour, conformément à l’encodage ci-dessus.

- Pour les types génériques, le nom du type est suivi d’un accent grave, puis d’un chiffre qui indique le nombre de paramètres de type générique. Par exemple :

     ``<member name="T:SampleClass`2">`` est l’étiquette pour un type qui est défini en tant que `public class SampleClass<T, U>`.

     Pour les méthodes qui prennent des types génériques en tant que paramètres, les paramètres de types génériques sont spécifiés sous forme de chiffres précédés d’accents graves (par exemple \`0,\`1). Chaque chiffre représente une notation de tableau de base zéro pour les paramètres génériques du type.

## <a name="examples"></a>Exemples

Les exemples suivants montrent comment les chaînes d’ID pour une classe et ses membres seraient générées :

[!code-csharp[csProgGuidePointers#21](~/samples/snippets/csharp/VS_Snippets_VBCSharp/csProgGuidePointers/CS/Pointers.cs#21)]

## <a name="see-also"></a>Voir aussi

- [Guide de programmation CMD](../index.md)
- [-doc (options de compilateur de C)](../../language-reference/compiler-options/doc-compiler-option.md)
- [Commentaires sur la documentation XML](./index.md)
