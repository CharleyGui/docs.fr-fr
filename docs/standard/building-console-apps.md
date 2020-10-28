---
title: Créer des applications console dans .NET
ms.date: 03/30/2017
ms.technology: dotnet-standard
helpviewer_keywords:
- .NET, creating console applications
- application development [.NET], console
- console applications
ms.assetid: c21fb997-9f0e-40a5-8741-f73bba376bd8
ms.openlocfilehash: b9c38e1311379037695879565b33ade29c6bf632
ms.sourcegitcommit: 279fb6e8d515df51676528a7424a1df2f0917116
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 10/27/2020
ms.locfileid: "92687551"
---
# <a name="console-apps-in-net"></a>Applications console dans .NET

Les applications .NET peuvent utiliser la <xref:System.Console?displayProperty=nameWithType> classe pour lire et écrire des caractères à partir de la console. Les données provenant de la console sont lues dans le flux d'entrée standard, les données à destination de la console sont écrites dans le flux de sortie standard et les données d'erreur à destination de la console sont écrites dans le flux de sortie standard des erreurs. Ces flux de données, associés automatiquement à la console au démarrage de l'application, sont présentés respectivement en tant que propriétés <xref:System.Console.In%2A>, <xref:System.Console.Out%2A> et <xref:System.Console.Error%2A>.

La valeur de la propriété <xref:System.Console.In%2A?displayProperty=nameWithType> est un objet <xref:System.IO.TextReader?displayProperty=nameWithType>, alors que les valeurs des propriétés <xref:System.Console.Out%2A?displayProperty=nameWithType> et <xref:System.Console.Error%2A?displayProperty=nameWithType> sont des objets <xref:System.IO.TextWriter?displayProperty=nameWithType>. Vous pouvez associer ces propriétés à des flux qui ne représentent pas la console, ce qui vous permet de désigner un autre emplacement pour les entrées ou les sorties. Par exemple, vous pouvez rediriger la sortie vers un fichier en définissant la propriété <xref:System.Console.Out%2A?displayProperty=nameWithType> sur un objet <xref:System.IO.StreamWriter?displayProperty=nameWithType>, qui encapsule un <xref:System.IO.FileStream?displayProperty=nameWithType> au moyen de la méthode <xref:System.Console.SetOut%2A?displayProperty=nameWithType>. Il n'est pas nécessaire que les propriétés <xref:System.Console.In%2A?displayProperty=nameWithType> et <xref:System.Console.Out%2A?displayProperty=nameWithType> fassent référence au même flux.

> [!NOTE]
> Pour plus d'informations sur la génération d'applications de console, notamment des exemples dans C#, Visual Basic et C++, consultez la documentation relative à la classe <xref:System.Console>.

Si la console n’existe pas, par exemple dans une application Windows Forms, la sortie écrite dans le flux de sortie standard n’est pas visible, car il n’y a aucune console dans laquelle écrire les informations. L'écriture d'informations sur une console inaccessible ne déclenche pas d'exception. (Vous pouvez toujours changer le type d’application en **application console** , par exemple, dans les pages de propriétés du projet dans Visual Studio).

La classe **System.Console** possède des méthodes qui peuvent lire des caractères ou des lignes complètes à partir de la console. D'autres méthodes convertissent des données et mettent en forme des chaînes, puis écrivent les chaînes mises en forme sur la console. Pour plus d’informations sur la mise en forme des chaînes, consultez [mise en forme des types](base-types/formatting-types.md).

> [!TIP]
> Les applications console ne disposent pas de pompe de messages démarrant par défaut. Par conséquent, les appels de console aux minuteries Microsoft Win32 peuvent échouer.

## <a name="see-also"></a>Voir aussi

- <xref:System.Console?displayProperty=nameWithType>
- [Mise en forme des types](base-types/formatting-types.md)
