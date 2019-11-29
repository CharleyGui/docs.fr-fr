---
title: Fournisseurs de type
description: Découvrez comment un F# fournisseur de type est un composant qui fournit des types, des propriétés et des méthodes à utiliser dans vos programmes.
ms.date: 04/02/2018
ms.openlocfilehash: 7fa0ff6b5f2b0bc978df2988f22b2042acc22320
ms.sourcegitcommit: 93762e1a0dae1b5f64d82eebb7b705a6d566d839
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 11/27/2019
ms.locfileid: "74552914"
---
# <a name="type-providers"></a>Fournisseurs de type

Un fournisseur de type F# est un composant qui fournit des types, des propriétés et des méthodes à utiliser dans votre programme. Les fournisseurs de type génèrent ce qui sont appelés **types fournis**, qui sont F# générés par le compilateur et qui sont basés sur une source de données externe.

Par exemple, un F# fournisseur de type pour SQL peut générer des types représentant des tables et des colonnes dans une base de données relationnelle. En fait, c’est ce que fait le fournisseur de type [SqlProvider](https://fsprojects.github.io/SQLProvider/) .

Les types fournis dépendent des paramètres d’entrée d’un fournisseur de type. Une telle entrée peut être un exemple de source de données (par exemple, un fichier de schéma JSON), une URL pointant directement vers un service externe ou une chaîne de connexion à une source de données. Un fournisseur de type peut également s’assurer que les groupes de types sont développés uniquement à la demande ; autrement dit, ils sont développés si les types sont réellement référencés par votre programme. Cela permet l'intégration directe et à la demande d'espaces d'informations à grande échelle, tels que les marchés de données en ligne, de manière fortement typée.

## <a name="generative-and-erased-type-providers"></a>Fournisseurs de type régénératif et effacés

Les fournisseurs de type sont de deux types : régénératif et effacé.

Les fournisseurs de type régénératif produisent des types qui peuvent être écrits en tant que types .NET dans l’assembly dans lequel ils sont produits. Cela leur permet d’être consommés à partir du code dans d’autres assemblys. Cela signifie que la représentation typée de la source de données doit en général être un qui peut être représenté avec les types .NET.

L’effacement des fournisseurs de type produit des types qui peuvent uniquement être consommés dans l’assembly ou le projet à partir duquel ils sont générés. Les types sont éphémères ; autrement dit, ils ne sont pas écrits dans un assembly et ne peuvent pas être utilisés par le code dans d’autres assemblys. Ils peuvent contenir des membres *RETARDÉS* , ce qui vous permet d’utiliser les types fournis à partir d’un espace d’informations potentiellement infini. Ils sont utiles pour utiliser un petit sous-ensemble d’une source de données importante et interconnectée.

## <a name="commonly-used-type-providers"></a>Fournisseurs de type couramment utilisés

Les bibliothèques couramment utilisées suivantes contiennent des fournisseurs de type pour différentes utilisations :

- [FSharp. Data](https://fsharp.github.io/FSharp.Data/) comprend des fournisseurs de type pour les formats et les ressources de documents JSON, XML, CSV et html.
- [SqlProvider](https://fsprojects.github.io/SQLProvider/) fournit un accès fortement typé aux bases de données relationnelles par le F# biais du mappage d’objets et des requêtes LINQ sur ces sources de données.
- [FSharp. Data. SqlClient](https://fsprojects.github.io/FSharp.Data.SqlClient/) possède un ensemble de fournisseurs de type pour l’incorporation activée de T-SQL dans au moment F#de la compilation dans.
- Le [fournisseur de type de stockage Azure](https://fsprojects.github.io/AzureStorageTypeProvider/) fournit des types pour les objets BLOB, les tables et les files d’attente Azure, ce qui vous permet d’accéder à ces ressources sans avoir à spécifier des noms de ressource en tant que chaînes dans votre programme.
- [FSharp. Data. GraphQL](https://fsprojects.github.io/FSharp.Data.GraphQL/index.html) contient le **GraphQLProvider**, qui fournit des types basés sur un serveur GRAPHQL spécifié par l’URL.

Le cas échéant, vous pouvez [créer vos propres fournisseurs de type personnalisés](creating-a-type-provider.md), ou référencer des fournisseurs de type qui ont été créés par d’autres. Par exemple, supposez que votre organisation dispose d'un service de données fournissant un nombre important et croissant de jeux de données nommées, chacun avec son propre schéma stable de données. Vous pouvez choisir de créer un fournisseur de type qui lit les schémas et présente les derniers groupes de données disponibles au programmeur de manière fortement typée.

## <a name="see-also"></a>Voir aussi

- [Didacticiel : créer un fournisseur de type](creating-a-type-provider.md)
- [Informations de référence sur le langage F#](../../language-reference/index.md)
