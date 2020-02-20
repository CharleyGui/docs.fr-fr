---
title: Outils supplémentaires
description: Vue d’ensemble des outils supplémentaires que vous pouvez installer, prenant en charge et étendant les fonctionnalités de .NET Core.
author: mlacouture
ms.date: 02/13/2020
ms.custom: mvc
ms.openlocfilehash: c0224a1cc6cbb9ae6fa88e5f869c47a1e84289e0
ms.sourcegitcommit: 700ea803fb06c5ce98de017c7f76463ba33ff4a9
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 02/19/2020
ms.locfileid: "77451523"
---
# <a name="net-core-additional-tools-overview"></a>Vue d’ensemble des outils .NET Core supplémentaires

Cette section compile une liste d’outils qui prennent en charge et étendent les fonctionnalités de .NET Core, en plus de la CLI .NET Core.

## <a name="net-core-uninstall-tool"></a>Outil de désinstallation de .NET Core

L' [outil de désinstallation de .net Core](https://github.com/dotnet/cli-lab/releases) (`dotnet-core-uninstall`) vous permet de nettoyer les kits de développement logiciel (SDK) .net Core et les runtimes sur un système de sorte que seules les versions spécifiées soient conservées. Une collection d’options est disponible pour spécifier les versions qui sont désinstallées.

## <a name="net-core-diagnostic-tools"></a>Outils de diagnostic .NET Core

[dotnet-Counters](../diagnostics/dotnet-counters.md) est un outil d’analyse des performances pour l’analyse de l’intégrité et des performances de premier niveau.

[dotnet-dump](../diagnostics/dotnet-dump.md) offre un moyen de collecter et d’analyser les vidages principaux Windows et Linux sans débogueur natif.

[dotnet-trace](../diagnostics/dotnet-trace.md) collecte les données de profilage de votre application qui peuvent vous aider dans des scénarios où vous devez déterminer ce qui entraîne l’exécution lente d’une application.

## <a name="wcf-web-service-reference-tool"></a>Outil de référence de service Web WCF

L’outil de référence de [service Web](wcf-web-service-reference-guide.md) WCF (Windows Communication Foundation) est un fournisseur de services connectés Visual Studio qui a fait ses débuts dans [Visual studio 2017 version 15,5](/visualstudio/releasenotes/vs2017-relnotes-v15.5#WCFTools). Cet outil récupère les métadonnées d’un service Web dans la solution actuelle, sur un emplacement réseau ou à partir d’un fichier WSDL. Il génère un fichier source compatible avec .NET Core, définissant une classe proxy WCF avec des méthodes que vous pouvez utiliser pour accéder aux opérations de service Web.

## <a name="wcf-dotnet-svcutil-tool"></a>Outil WCF dotnet-Svcutil

L' [outil WCF dotnet-Svcutil](dotnet-svcutil-guide.md) est un outil .net qui récupère les métadonnées d’un service Web sur un emplacement réseau ou à partir d’un fichier WSDL. Il génère un fichier source compatible avec .NET Core, définissant une classe proxy WCF avec des méthodes que vous pouvez utiliser pour accéder aux opérations de service Web.

L’outil **dotnet-Svcutil** est une alternative à la [**Référence du service Web WCF**](wcf-web-service-reference-guide.md) du fournisseur de services connectés Visual Studio, qui a été livré avec visual studio 2017 version 15,5. L’outil **dotnet-Svcutil** , en tant qu’outil .net, est disponible sur Linux, MacOS et Windows.

## <a name="wcf-dotnet-svcutilxmlserializer-tool"></a>WCF dotnet-Svcutil. XmlSerializer (outil)

Sur le .NET Framework, vous pouvez prégénérer un assembly de sérialisation à l’aide de l’outil svcutil. L' [outil WCF dotnet-Svcutil. XmlSerializer](dotnet-svcutil.xmlserializer-guide.md) offre des fonctionnalités similaires sur .net core. Il prégénère un code de sérialisation C# pour les types dans l’application cliente qui sont utilisés par le contrat de service WCF et qui peuvent être sérialisés par <xref:System.Xml.Serialization.XmlSerializer>. Cela améliore les performances de démarrage de la sérialisation XML lors de la sérialisation ou de la désérialisation de ces types d’objets.

## <a name="xml-serializer-generator"></a>Générateur de sérialiseur XML

Comme le [Générateur de sérialiseur XML (sgen.exe)](../../standard/serialization/xml-serializer-generator-tool-sgen-exe.md) pour le .NET Framework, le [package NuGet Microsoft.XmlSerializer.Generator](https://www.nuget.org/packages/Microsoft.XmlSerializer.Generator) est la solution pour les bibliothèques .NET Core et .NET Standard. Il crée un assembly de sérialisation XML pour les types contenus dans un assembly afin d’améliorer les performances de démarrage de la sérialisation XML pendant la sérialisation ou la désérialisation des objets de ces types avec <xref:System.Xml.Serialization.XmlSerializer>.
