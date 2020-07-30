---
title: Traitement du fichier XML-Guide de programmation C#
description: En savoir plus sur le traitement du fichier XML en programmation C#. Consultez des exemples de code et affichez des ressources disponibles supplémentaires.
ms.date: 07/20/2015
helpviewer_keywords:
- XML processing [C#]
- XML [C#], processing
ms.assetid: 60c71193-9dac-4cd3-98c5-100bd0edcc42
ms.openlocfilehash: 6f8a278ed842cd9c4176f3efff423ee048f7e9b9
ms.sourcegitcommit: 552b4b60c094559db9d8178fa74f5bafaece0caf
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 07/29/2020
ms.locfileid: "87381539"
---
# <a name="process-the-xml-file-c-programming-guide"></a>Traiter le fichier XML (Guide de programmation C#)

Le compilateur génère une chaîne d’ID pour chaque construction de votre code balisée pour générer la documentation. (Pour plus d’informations sur la façon de baliser votre code, consultez [Balises recommandées pour les commentaires de documentation](./recommended-tags-for-documentation-comments.md).) La chaîne d’ID identifie de façon unique la construction. Les programmes qui traitent le fichier XML peuvent utiliser la chaîne d’ID pour identifier les métadonnées .NET ou l’élément de réflexion correspondants auxquels la documentation s’applique.

## <a name="id-strings"></a>Chaînes d’ID

Le fichier XML n’est pas une représentation hiérarchique de votre code. Il s’agit d’une liste plate qui a un ID généré pour chaque élément.

Le compilateur respecte les règles suivantes quand il génère les chaînes d’ID :

- La chaîne ne contient aucun espace blanc.

- La première partie de la chaîne identifie le type de membre à l’aide d’un caractère unique suivi d’un signe deux-points. Les types de membres suivants sont utilisés :

    |Caractère|Type de membre|Notes|
    |---------------|-----------------|-|
    |N|espace de noms|Vous ne pouvez pas ajouter de commentaires de documentation à un espace de noms, mais vous pouvez faire des références cref à des commentaires, si cela est pris en charge.|
    |T|type|Un type peut être une classe, une interface, un struct, une énumération ou un délégué.|
    |F|field|
    |P|propriété|Comprend des indexeurs ou d’autres propriétés indexées.|
    |M|method|Comprend des méthodes spéciales, telles que des constructeurs et des opérateurs.|
    |E|événement|
    |!|chaîne d’erreur|Le reste de la chaîne fournit des informations sur l’erreur. Le compilateur C# génère des informations d’erreur pour les liens qui ne peuvent pas être résolus.|

- La deuxième partie de la chaîne est le nom qualifié complet de l’élément, en commençant à la racine de l’espace de noms. Le nom de l’élément, ses types englobants et l’espace de noms sont séparés par des points. Si le nom de l’élément lui-même comporte des points, ceux-ci sont remplacés par un signe dièse (« # »). Il est supposé qu’aucun élément n’a de signature de hachage directement dans son nom. Par exemple, le nom qualifié complet du constructeur de chaîne est « System. String. #ctor ».

- Pour les propriétés et les méthodes, la liste de paramètres entre parenthèses suit. S’il n’y a aucun paramètre, aucune parenthèse n’est présente. Les paramètres sont séparés par des virgules. L’encodage de chaque paramètre suit directement la manière dont il est encodé dans une signature .NET :

  - Types de base. Les types réguliers (ELEMENT_TYPE_CLASS ou ELEMENT_TYPE_VALUETYPE) sont représentés en tant que nom qualifié complet du type.

  - Les types intrinsèques (par exemple, ELEMENT_TYPE_I4, ELEMENT_TYPE_OBJECT, ELEMENT_TYPE_STRING, ELEMENT_TYPE_TYPEDBYREF et ELEMENT_TYPE_VOID) sont représentés en tant que nom qualifié complet du type complet correspondant. Par exemple, System.Int32 ou System.TypedReference.

  - ELEMENT_TYPE_PTR est représenté par un « \* » après le type modifié.

  - ELEMENT_TYPE_BYREF est représenté par un '\@' après le type modifié.

  - ELEMENT_TYPE_PINNED est représenté par un « ^ » après le type modifié. Le compilateur C# ne génère jamais ceci.

  - ELEMENT_TYPE_CMOD_REQ est représenté par un « &#124; » et le nom qualifié complet de la classe de modification, après le type modifié. Le compilateur C# ne génère jamais ceci.

  - ELEMENT_TYPE_CMOD_OPT est représenté par un « ! » et le nom qualifié complet de la classe de modification, après le type modifié.

  - ELEMENT_TYPE_SZARRAY est représenté par « [] » après le type d’élément du tableau.

  - ELEMENT_TYPE_GENERICARRAY est représenté par « [?] » après le type d’élément du tableau. Le compilateur C# ne génère jamais ceci.

  - ELEMENT_TYPE_ARRAY est représenté sous la*forme [Lower*: `size` , Lower :*lowerbound* `size` ], où le nombre de virgules est le rang-1, et les limites inférieures et la taille de chaque dimension, si elles sont connues, sont représentées au format décimal. Si une limite inférieure ou une taille n’est pas spécifiée, elle est omise. Si la limite inférieure et la taille d’une dimension particulière sont omises, le « : » est également omis. Par exemple, un tableau à deux dimensions avec 1 comme limite inférieure et une taille non spécifiée est [1:,1:].

  - ELEMENT_TYPE_FNPTR est représenté en tant que « =FUNC:`type`(*signature*) », où `type` est le type de retour et *signature* correspond aux arguments de la méthode. S’il n’y a pas d’argument, les parenthèses sont omises. Le compilateur C# ne génère jamais ceci.

  Les composants de signature suivants ne sont pas représentés, car ils ne sont pas utilisés pour différencier les méthodes surchargées :

  - convention d’appel

  - type de retour

  - ELEMENT_TYPE_SENTINEL

- Pour les opérateurs de conversion uniquement ( `op_Implicit` et `op_Explicit` ), la valeur de retour de la méthode est encodée sous la forme d’un « ~ » suivi du type de retour.

- Pour les types génériques, le nom du type est suivi d’un accent grave, puis d’un chiffre qui indique le nombre de paramètres de type générique. Par exemple :

     ``<member name="T:SampleClass`2">`` est l’étiquette pour un type qui est défini en tant que `public class SampleClass<T, U>`.

     Pour les méthodes qui prennent des types génériques comme paramètres, les paramètres de type générique sont spécifiés sous la forme de nombres précédés d’impulsions (par exemple \` , 0, \` 1). Chaque nombre représente une notation de tableau de base zéro pour les paramètres génériques du type.

## <a name="examples"></a>Exemples

Les exemples suivants montrent comment les chaînes d’ID pour une classe et ses membres sont générées :

[!code-csharp[csProgGuidePointers#21](~/samples/snippets/csharp/VS_Snippets_VBCSharp/csProgGuidePointers/CS/Pointers.cs#21)]

## <a name="see-also"></a>Voir aussi

- [Guide de programmation C#](../index.md)
- [-doc (options du compilateur C#)](../../language-reference/compiler-options/doc-compiler-option.md)
- [Commentaires sur la documentation XML](./index.md)
