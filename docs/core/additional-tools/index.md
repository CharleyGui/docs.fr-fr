---
title: Autres outils d’interface CLI .NET Core
description: Vue d’ensemble des outils supplémentaires que vous pouvez installer, prenant en charge et étendant les fonctionnalités de .NET Core.
author: mlacouture
ms.date: 11/27/2018
ms.custom: mvc, seodec18
ms.openlocfilehash: c885d6f6b0417a80dd6e26afe9572766738c5b4b
ms.sourcegitcommit: 559259da2738a7b33a46c0130e51d336091c2097
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 10/22/2019
ms.locfileid: "72771966"
---
# <a name="net-core-additional-tools-overview"></a>Vue d’ensemble des outils .NET Core supplémentaires

Cette section dresse une liste des outils qui prennent en charge et étendent les fonctionnalités de .NET Core, en plus des outils d’[interface de ligne de commande (CLI) .NET Core](../tools/index.md).

## <a name="wcf-web-service-reference-toolwcf-web-service-reference-guidemd"></a>[Outil WCF Web Service Reference](wcf-web-service-reference-guide.md)

WCF (Windows Communication Foundation) Web Service Reference est un fournisseur de services connectés Visual Studio qui a fait son apparition dans [Visual Studio 2017 version 15.5](/visualstudio/releasenotes/vs2017-relnotes-v15.5#WCFTools). Cet outil récupère les métadonnées d’un service web dans la solution actuelle sur un emplacement réseau ou dans un fichier WSDL, puis génère un fichier source compatible avec .NET Core, en définissant une classe proxy WCF avec des méthodes que vous pouvez utiliser pour accéder aux opérations du service web.

## <a name="wcf-dotnet-svcutil-tooldotnet-svcutil-guidemd"></a>[Outil dotnet-svcutil WCF](dotnet-svcutil-guide.md)

L’outil dotnet-svcutil WCF (Windows Communication Foundation) est un outil CLI .NET Core qui récupère les métadonnées d’un service web sur un emplacement réseau ou dans un fichier WSDL, puis génère un fichier source compatible avec .NET Core, en définissant une classe proxy WCF avec des méthodes que vous pouvez utiliser pour accéder aux opérations du service web.
L’outil **dotnet-Svcutil** est une autre option pour la [**Référence du service Web WCF**](wcf-web-service-reference-guide.md) du fournisseur de services connectés Visual Studio, qui a été livré avec visual studio 2017 version 15,5. L’outil **dotnet-svcutil**, en tant qu’outil CLI .NET Core, est disponible sur les plateformes Linux, macOS et Windows.

## <a name="wcf-dotnet-svcutilxmlserializer-tooldotnet-svcutilxmlserializer-guidemd"></a>[Outil dotnet-svcutil.xmlserializer WCF](dotnet-svcutil.xmlserializer-guide.md)

Sur le .NET Framework, vous pouvez prégénérer un assembly de sérialisation à l’aide de l’outil svcutil. Le package NuGet dotnet-svcutil.xmlserializer fournit des fonctionnalités similaires sur .NET Core. Il prégénère un code de sérialisation C# pour les types dans l’application cliente qui sont utilisés par le contrat de service WCF et qui peuvent être sérialisés par <xref:System.Xml.Serialization.XmlSerializer>. Cela améliore les performances de démarrage de la sérialisation XML lors de la sérialisation ou de la désérialisation de ces types d’objets.

## <a name="xml-serializer-generatorxml-serializer-generatormd"></a>[Générateur de sérialiseur XML](xml-serializer-generator.md)

Comme le [Générateur de sérialiseur XML (sgen.exe)](../../standard/serialization/xml-serializer-generator-tool-sgen-exe.md) pour le .NET Framework, le [package NuGet Microsoft.XmlSerializer.Generator](https://www.nuget.org/packages/Microsoft.XmlSerializer.Generator) est la solution pour les bibliothèques .NET Core et .NET Standard. Il crée un assembly de sérialisation XML pour les types contenus dans un assembly afin d’améliorer les performances de démarrage de la sérialisation XML pendant la sérialisation ou la désérialisation des objets de ces types avec <xref:System.Xml.Serialization.XmlSerializer>.
