---
title: Outils CLI supplémentaires
description: Vue d’ensemble des outils supplémentaires que vous pouvez installer, prenant en charge et étendant les fonctionnalités de .NET Core.
author: mlacouture
ms.date: 12/02/2019
ms.custom: mvc
ms.openlocfilehash: 853633f5ef159eee39ed1a8682372d4291a752f5
ms.sourcegitcommit: de17a7a0a37042f0d4406f5ae5393531caeb25ba
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 01/24/2020
ms.locfileid: "76740709"
---
# <a name="net-core-additional-tools-overview"></a>Vue d’ensemble des outils .NET Core supplémentaires

Cette section dresse une liste des outils qui prennent en charge et étendent les fonctionnalités de .NET Core, en plus des outils d’[interface de ligne de commande (CLI) .NET Core](../tools/index.md).

## <a name="net-core-uninstall-tooluninstall-toolmd"></a>[Outil de désinstallation de .NET Core](uninstall-tool.md)

L' [outil de désinstallation de .net Core](https://github.com/dotnet/cli-lab/releases) (`dotnet-core-uninstall`) vous permet de nettoyer les kits de développement logiciel (SDK) .net Core et les runtimes sur un système de sorte que seules les versions spécifiées soient conservées. Une collection d’options est disponible pour spécifier les versions qui sont désinstallées.

## <a name="wcf-web-service-reference-toolwcf-web-service-reference-guidemd"></a>[Outil WCF Web Service Reference](wcf-web-service-reference-guide.md)

WCF (Windows Communication Foundation) Web Service Reference est un fournisseur de services connectés Visual Studio qui a fait son apparition dans [Visual Studio 2017 version 15.5](/visualstudio/releasenotes/vs2017-relnotes-v15.5#WCFTools). Cet outil récupère les métadonnées d’un service Web dans la solution actuelle, sur un emplacement réseau ou à partir d’un fichier WSDL. Il génère un fichier source compatible avec .NET Core, définissant une classe proxy WCF avec des méthodes que vous pouvez utiliser pour accéder aux opérations de service Web.

## <a name="wcf-dotnet-svcutil-tooldotnet-svcutil-guidemd"></a>[Outil dotnet-svcutil WCF](dotnet-svcutil-guide.md)

L’outil WCF (Windows Communication Foundation) dotnet-Svcutil est un outil CLI .NET Core qui récupère les métadonnées d’un service Web sur un emplacement réseau ou à partir d’un fichier WSDL. Il génère un fichier source compatible avec .NET Core, définissant une classe proxy WCF avec des méthodes que vous pouvez utiliser pour accéder aux opérations de service Web.

L’outil **dotnet-Svcutil** est une autre option pour la [**Référence du service Web WCF**](wcf-web-service-reference-guide.md) du fournisseur de services connectés Visual Studio, qui a été livré avec visual studio 2017 version 15,5. L’outil **dotnet-Svcutil** , en tant qu’outil de CLI .net Core, est disponible sur plusieurs plateformes sur Linux, MacOS et Windows.

## <a name="wcf-dotnet-svcutilxmlserializer-tooldotnet-svcutilxmlserializer-guidemd"></a>[Outil dotnet-svcutil.xmlserializer WCF](dotnet-svcutil.xmlserializer-guide.md)

Sur le .NET Framework, vous pouvez prégénérer un assembly de sérialisation à l’aide de l’outil svcutil. Le package NuGet dotnet-svcutil.xmlserializer fournit des fonctionnalités similaires sur .NET Core. Il prégénère un code de sérialisation C# pour les types dans l’application cliente qui sont utilisés par le contrat de service WCF et qui peuvent être sérialisés par <xref:System.Xml.Serialization.XmlSerializer>. Cela améliore les performances de démarrage de la sérialisation XML lors de la sérialisation ou de la désérialisation de ces types d’objets.

## <a name="xml-serializer-generatorxml-serializer-generatormd"></a>[Générateur de sérialiseur XML](xml-serializer-generator.md)

Comme le [Générateur de sérialiseur XML (sgen.exe)](../../standard/serialization/xml-serializer-generator-tool-sgen-exe.md) pour le .NET Framework, le [package NuGet Microsoft.XmlSerializer.Generator](https://www.nuget.org/packages/Microsoft.XmlSerializer.Generator) est la solution pour les bibliothèques .NET Core et .NET Standard. Il crée un assembly de sérialisation XML pour les types contenus dans un assembly afin d’améliorer les performances de démarrage de la sérialisation XML pendant la sérialisation ou la désérialisation des objets de ces types avec <xref:System.Xml.Serialization.XmlSerializer>.
