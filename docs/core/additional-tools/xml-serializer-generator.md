---
title: Microsoft XML Serializer Generator
description: Vue d’ensemble de Microsoft XML Serializer Generator. Utilisez XML Serializer Generator afin de générer un assembly de sérialisation XML pour les types contenus dans votre projet.
author: mlacouture
ms.date: 01/19/2017
ms.topic: tutorial
ms.custom: mvc
ms.openlocfilehash: 094dd1227033e167050ad73121b3005a592a0ae4
ms.sourcegitcommit: 7588136e355e10cbc2582f389c90c127363c02a5
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 03/14/2020
ms.locfileid: "75714526"
---
# <a name="using-microsoft-xml-serializer-generator-on-net-core"></a>Utilisation de Microsoft XML Serializer Generator sur .NET Core

Ce didacticiel montre comment utiliser Microsoft XML Serializer Generator dans une application C# .NET Core. Au cours de ce didacticiel, vous apprenez à :

> [!div class="checklist"]
>
> - Créer une application .NET Core
> - Ajouter une référence au package Microsoft.XmlSerializer.Generator
> - Modifier votre fichier MyApp.csproj pour ajouter des dépendances
> - Ajouter une classe et un XmlSerializer
> - Générer et exécuter l’application

Comme l’outil [XML Serializer Generator (sgen.exe)](../../standard/serialization/xml-serializer-generator-tool-sgen-exe.md) pour le .NET Framework, le [package NuGet Microsoft.XmlSerializer.Generator](https://www.nuget.org/packages/Microsoft.XmlSerializer.Generator) est l’équivalent pour les projets .NET Core et .NET Standard. Il crée un assembly de sérialisation XML pour les types contenus dans un assembly afin d’améliorer les performances de démarrage de la sérialisation XML pendant la sérialisation ou la désérialisation des objets de ces types avec <xref:System.Xml.Serialization.XmlSerializer>.

## <a name="prerequisites"></a>Conditions préalables requises

Pour suivre ce tutoriel :

- [.NET Core 2.1 SDK](https://dotnet.microsoft.com/download) ou plus tard.
- Votre éditeur de code favori.

> [!TIP]
> Vous avez besoin d’installer un éditeur de code ? Essayez [Visual Studio](https://aka.ms/vsdownload?utm_source=mscom&utm_campaign=msdocs) !

## <a name="use-microsoft-xml-serializer-generator-in-a-net-core-console-application"></a>Utiliser Microsoft XML Serializer Generator dans une application console .NET Core

Les instructions suivantes montrent comment utiliser XML Serializer Generator dans une application console .NET Core.

### <a name="create-a-net-core-console-application"></a>Créer une application console .NET Core

Ouvrez une invite de commandes et créez un dossier nommé *MyApp*. Accédez au dossier créé et tapez la commande suivante :

```dotnetcli
dotnet new console
```

### <a name="add-a-reference-to-the-microsoftxmlserializergenerator-package-in-the-myapp-project"></a>Ajouter une référence au package Microsoft.XmlSerializer.Generator dans le projet MyApp

Utilisez [`dotnet add package`](../tools//dotnet-add-package.md) la commande pour ajouter la référence dans votre projet.

Tapez :

```dotnetcli
dotnet add package Microsoft.XmlSerializer.Generator -v 1.0.0
```

### <a name="verify-changes-to-myappcsproj-after-adding-the-package"></a>Vérifier les modifications apportées à MyApp.csproj après l’ajout du package

Ouvrez votre éditeur de code et c’est parti ! Nous travaillons encore à partir du répertoire *MyApp* dans lequel nous avons créé l’application.

Ouvrez *MyApp.csproj* dans votre éditeur de texte.

Après avoir [`dotnet add package`](../tools//dotnet-add-package.md) couru la commande, les lignes suivantes sont ajoutées à votre fichier de projet *MyApp.csproj* :

 ```xml
 <ItemGroup>
    <PackageReference Include="Microsoft.XmlSerializer.Generator" Version="1.0.0" />
 </ItemGroup>
 ```

### <a name="add-another-itemgroup-section-for-net-core-cli-tool-support"></a>Ajouter une autre section ItemGroup pour la prise en charge de l’outil d’interface CLI .NET Core

Ajoutez les lignes suivantes après la section `ItemGroup` que nous avons inspectée :

 ```xml
 <ItemGroup>
    <DotNetCliToolReference Include="Microsoft.XmlSerializer.Generator" Version="1.0.0" />
 </ItemGroup>
 ```

### <a name="add-a-class-in-the-application"></a>Ajouter une classe dans l’application

Ouvrez *Program.cs* dans votre éditeur de texte. Ajoutez la classe nommée *MyClass* dans *Program.cs*.

```csharp
public class MyClass
{
   public int Value;
}
```

### <a name="create-an-xmlserializer-for-myclass"></a>Créer un `XmlSerializer` pour MyClass

Ajoutez la ligne suivante à l’intérieur de *Main* pour créer un `XmlSerializer` pour MyClass :

```csharp
var serializer = new System.Xml.Serialization.XmlSerializer(typeof(MyClass));
```

### <a name="build-and-run-the-application"></a>Génération et exécution de l’application

Toujours dans le dossier *MyApp*, exécutez l’application avec [`dotnet run`](../tools/dotnet-run.md). Elle se charge automatiquement et utilise les sérialiseurs prégénérés au moment de l’exécution.

Tapez la commande suivante dans la fenêtre de console :

```dotnetcli
dotnet run
```

> [!NOTE]
> [`dotnet run`](../tools/dotnet-run.md)appels [`dotnet build`](../tools/dotnet-build.md) pour s’assurer que les cibles `dotnet <assembly.dll>` de construction ont été construites, puis les appels pour exécuter l’application cible.

> [!IMPORTANT]
> Les commandes et les étapes indiquées dans ce didacticiel pour exécuter votre application sont utilisées uniquement au moment du développement. Une fois que vous êtes prêt à déployer votre application, consultez les différentes [stratégies de déploiement](../deploying/index.md) pour les applications .NET Core et la commande [`dotnet publish`](../tools/dotnet-publish.md).

Si tout fonctionne, un assembly nommé *MyApp.XmlSerializers.dll* est généré dans le dossier de sortie.

Félicitations ! Vous venez de :
> [!div class="checklist"]
>
> - Créer une application .NET Core
> - Ajouter une référence au package Microsoft.XmlSerializer.Generator
> - Modifier votre fichier MyApp.csproj pour ajouter des dépendances
> - Ajouter une classe et un XmlSerializer
> - Générer et exécuter l’application

## <a name="related-resources"></a>Ressources associées

- [Introduction à la sérialisation XML](../../standard/serialization/introducing-xml-serialization.md)
- [Comment sérialiser à l’aide de XmlSerializer (C)](../../csharp/programming-guide/concepts/linq/how-to-serialize-using-xmlserializer.md)
- [Guide pratique pour sérialiser à l’aide de XmlSerializer (Visual Basic)](../../visual-basic/programming-guide/concepts/linq/how-to-serialize-using-xmlserializer.md)
