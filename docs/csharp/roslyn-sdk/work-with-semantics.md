---
title: Utiliser le modèle sémantique du SDK .NET Compiler Platform
description: Cette présentation fournit des informations sur le type que vous utilisez pour comprendre et manipuler le modèle sémantique de votre code.
ms.date: 10/15/2017
ms.custom: mvc
ms.openlocfilehash: 8575988cd98a4c0ba3f24107788f065f7472f55d
ms.sourcegitcommit: 7588136e355e10cbc2582f389c90c127363c02a5
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 03/14/2020
ms.locfileid: "79156933"
---
# <a name="work-with-semantics"></a>Utiliser la sémantique

Les [arborescences de syntaxe](work-with-syntax.md) représentent la structure lexicale et syntaxique du code source. Cette information est suffisante pour décrire toutes les déclarations et la logique utilisées dans le code source, mais elle ne l’est pas pour identifier l’élément référencé. Un nom peut représenter les éléments suivants :

- Un type
- Un champ
- Une méthode
- Une variable locale

Ces éléments se distinguent par des caractéristiques uniques. Toutefois, pour déterminer à quel élément un identificateur fait réellement référence, avoir une connaissance approfondie des règles de langage s’avère souvent indispensable.

Certains éléments de programme sont représentés dans le code source, mais les programmes peuvent aussi faire référence à des bibliothèques précédemment compilées, empaquetées dans des fichiers d’assembly. Il n’y a pas de code source et donc pas d’arborescences ni nœuds de syntaxe disponibles pour les assemblys, mais les programmes peuvent faire référence à des éléments qu’ils contiennent.

Pour ces tâches, vous devez utiliser le **modèle sémantique**.

Par rapport à un modèle syntaxique du code source, un modèle sémantique encapsule en plus les règles de langage, ce qui vous aide à associer correctement les identificateurs avec l’élément de programme référencé.

## <a name="compilation"></a>Compilation

Une compilation est une représentation de tous les éléments nécessaires à la compilation d’un programme C# ou Visual Basic, à savoir l’ensemble des références d’assembly, des options du compilateur et des fichiers sources.

Toutes ces informations étant stockées au même emplacement, les éléments contenus dans le code source peuvent être décrits plus en détail. La compilation représente chaque élément déclaré (type, membre ou variable) sous forme de symbole. La compilation contient diverses méthodes qui vous aident à trouver et associer les symboles qui ont été déclarés dans le code source, ou importés en tant que métadonnées à partir d’un assembly.

De la même façon que les arborescences de syntaxe, les compilations sont immuables. Une fois créée, une compilation ne peut plus être modifiée, que ce soit par vous ou par tout autre utilisateur avec qui vous la partagez. Toutefois, vous pouvez créer une autre compilation à partir d’une compilation existante, en y apportant la modification souhaitée. Par exemple, vous pouvez créer une compilation semblable en tous points à une compilation existante, mais y ajouter un fichier source ou une référence d’assembly supplémentaire.

## <a name="symbols"></a>Symboles

Un symbole représente un élément distinct qui est déclaré dans le code source, ou importé en tant que métadonnées à partir d’un assembly. Chaque élément (espace de noms, type, méthode, propriété, champ, événement, paramètre ou variable locale) est représenté par un symbole.

Diverses méthodes et propriétés du type <xref:Microsoft.CodeAnalysis.Compilation> vous aident à trouver les symboles. Par exemple, vous pouvez rechercher un symbole d’un type déclaré par son nom de métadonnées commun. Vous pouvez aussi accéder à la table de symboles entière comme une arborescence de symboles ayant pour racine l’espace de noms global.

Les symboles contiennent également des informations supplémentaires que le compilateur collecte à partir du code source ou des métadonnées, par exemple, les autres symboles référencés. Chaque genre de symbole est représenté par une interface distincte dérivée de l’interface <xref:Microsoft.CodeAnalysis.ISymbol>, qui a ses propres méthodes et propriétés pour décrire en détail les informations collectées par le compilateur. Nombre de ces propriétés référencent directement d’autres symboles. Par exemple, la propriété <xref:Microsoft.CodeAnalysis.IMethodSymbol.ReturnType?displayProperty=nameWithType> indique quel symbole de type est référencé par la déclaration de méthode.

Les symboles fournissent une représentation des espaces de noms, types et membres commune au code source et aux métadonnées. Par exemple, une méthode déclarée dans le code source et une méthode importée des métadonnées sont toutes les deux représentées par un symbole <xref:Microsoft.CodeAnalysis.IMethodSymbol> ayant les mêmes propriétés.

Sur un plan conceptuel, les symboles sont similaires au système de type CLR représenté par l’API <xref:System.Reflection>, mais ils sont plus complets dans la mesure où ils modélisent d’autres éléments que des types. Les espaces de noms, les variables locales et les étiquettes sont tous des symboles. De plus, les symboles sont une représentation des concepts du langage, pas des concepts du CLR. Il y a beaucoup de similitudes, mais aussi de nombreuses différences importantes. Par exemple, une méthode d’itérateur en C# ou Visual Basic est un symbole unique. Quand la méthode d’itérateur est convertie en métadonnées CLR, elle devient un type avec plusieurs méthodes.

## <a name="semantic-model"></a>Modèle sémantique

Un modèle sémantique représente toutes les informations sémantiques relatives à un fichier source unique. Vous pouvez utiliser ce modèle pour découvrir les éléments suivants :

- Les symboles référencés à un emplacement spécifique dans le code source.
- Le type résultant d’une expression.
- Tous les diagnostics (erreurs et avertissements).
- Les flux entrants et sortants des variables dans les régions du code source.
- Les réponses à des questions plus spéculatives.
