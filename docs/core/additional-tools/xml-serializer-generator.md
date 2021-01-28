---
title: Microsoft XML Serializer Generator
description: Vue d’ensemble de Microsoft XML Serializer Generator. Utilisez XML Serializer Generator afin de générer un assembly de sérialisation XML pour les types contenus dans votre projet.
author: honggit
ms.date: 01/19/2017
ms.topic: tutorial
ms.custom: mvc
ms.openlocfilehash: 4b408326bb9f1bc3b82acb92e8daabfd90be43f6
ms.sourcegitcommit: 7e42488c2f8f63f6d499b5f8fb1dec5bac9ad254
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 01/28/2021
ms.locfileid: "98957895"
---
# <a name="using-microsoft-xml-serializer-generator-on-net-core"></a>Utilisation de Microsoft XML Serializer Generator sur .NET Core

Ce didacticiel montre comment utiliser Microsoft XML Serializer Generator dans une application C# .NET Core. Au cours de ce didacticiel, vous apprenez à :

> [!div class="checklist"]
>
> - Guide pratique pour créer une application .NET Core
> - Guide pratique pour ajouter une référence au package Microsoft.XmlSerializer.Generator
> - Guide pratique pour modifier votre fichier MyApp.csproj afin d’ajouter des dépendances
> - Guide pratique pour ajouter une classe et un XmlSerializer
> - Guide pratique pour générer et exécuter l’application

Comme l’outil [XML Serializer Generator (sgen.exe)](../../standard/serialization/xml-serializer-generator-tool-sgen-exe.md) pour le .NET Framework, le [package NuGet Microsoft.XmlSerializer.Generator](https://www.nuget.org/packages/Microsoft.XmlSerializer.Generator) est l’équivalent pour les projets .NET Core et .NET Standard. Il crée un assembly de sérialisation XML pour les types contenus dans un assembly afin d’améliorer les performances de démarrage de la sérialisation XML pendant la sérialisation ou la désérialisation des objets de ces types avec <xref:System.Xml.Serialization.XmlSerializer>.

## <a name="prerequisites"></a>Prérequis

Pour suivre ce tutoriel :

- [.Net Core 2,1 SDK](https://dotnet.microsoft.com/download) ou version ultérieure.
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

Utilisez la [`dotnet add package`](../tools/dotnet-add-package.md) commande pour ajouter la référence dans votre projet.

Tapez :

```dotnetcli
dotnet add package Microsoft.XmlSerializer.Generator -v 1.0.0
```

### <a name="verify-changes-to-myappcsproj-after-adding-the-package"></a>Vérifier les modifications apportées à MyApp.csproj après l’ajout du package

Ouvrez votre éditeur de code et c’est parti ! Nous travaillons encore à partir du répertoire *MyApp* dans lequel nous avons créé l’application.

Ouvrez *MyApp.csproj* dans votre éditeur de texte.

Après avoir exécuté la [`dotnet add package`](../tools/dotnet-add-package.md) commande, les lignes suivantes sont ajoutées à votre fichier projet *MyApp. csproj* :

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

Toujours dans le dossier *MyApp* , exécutez l’application via [`dotnet run`](../tools/dotnet-run.md) et elle charge automatiquement et utilise les sérialiseurs prégénérés au moment de l’exécution.

Tapez la commande suivante dans la fenêtre de console :

```dotnetcli
dotnet run
```

> [!NOTE]
> [`dotnet run`](../tools/dotnet-run.md) appelle [`dotnet build`](../tools/dotnet-build.md) pour s’assurer que les cibles de génération ont été générées, puis appelle `dotnet <assembly.dll>` pour exécuter l’application cible.

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
- [Comment sérialiser à l’aide de XmlSerializer (C#)](../../standard/linq/serialize-xmlserializer.md)
- [Guide pratique pour sérialiser à l’aide de XmlSerializer (Visual Basic)](../../standard/linq/serialize-xmlserializer.md)
