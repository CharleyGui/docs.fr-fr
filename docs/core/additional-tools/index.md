---
title: Outils supplémentaires
description: Vue d’ensemble des outils supplémentaires que vous pouvez installer, prenant en charge et étendant les fonctionnalités de .NET Core.
author: mlacouture
ms.date: 02/13/2020
ms.custom: mvc
ms.openlocfilehash: c0224a1cc6cbb9ae6fa88e5f869c47a1e84289e0
ms.sourcegitcommit: 7588136e355e10cbc2582f389c90c127363c02a5
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 03/15/2020
ms.locfileid: "77451523"
---
# <a name="net-core-additional-tools-overview"></a>Vue d’ensemble des outils .NET Core supplémentaires

Cette section compile une liste d’outils qui prennent en charge et prolongent la fonctionnalité .NET Core, en plus de l’ICI CLI core .NET.

## <a name="net-core-uninstall-tool"></a>Outil de désinstallation de .NET Core

[L’outil .NET Core Uninstall](https://github.com/dotnet/cli-lab/releases) (`dotnet-core-uninstall`) vous permet de nettoyer .NET Core SDKs et Runtimes sur un système de telle sorte que seules les versions spécifiées restent. Une collection d’options est disponible pour spécifier quelles versions sont non bloquées.

## <a name="net-core-diagnostic-tools"></a>.NET Outils diagnostiques de base

[dotnet-counters](../diagnostics/dotnet-counters.md) est un outil de surveillance des performances pour la surveillance de la santé de premier niveau et l’enquête sur le rendement.

[dotnet-dump](../diagnostics/dotnet-dump.md) fournit un moyen de collecter et d’analyser windows et Linux décharges de base sans un débbugger natif.

[dotnet-trace](../diagnostics/dotnet-trace.md) recueille des données de profilage de votre application qui peuvent vous aider dans des scénarios où vous devez savoir quelles sont les causes d’une application à fonctionner lentement.

## <a name="wcf-web-service-reference-tool"></a>Outil de référence du service Web WCF

L’outil de référence [des services Web](wcf-web-service-reference-guide.md) WCF (Windows Communication Foundation) est un fournisseur de services connectés Visual Studio qui a fait ses débuts dans [visual Studio 2017 version 15.5](/visualstudio/releasenotes/vs2017-relnotes-v15.5#WCFTools). Cet outil récupère les métadonnées d’un service web dans la solution actuelle, sur un emplacement réseau ou à partir d’un fichier WSDL. Il génère un fichier source compatible avec .NET Core, définissant une classe de proxy WCF avec des méthodes que vous pouvez utiliser pour accéder aux opérations de service Web.

## <a name="wcf-dotnet-svcutil-tool"></a>Outil dotnet-svcutil WCF

L’outil WCF [dotnet-svcutil](dotnet-svcutil-guide.md) est un outil .NET qui récupère les métadonnées d’un service Web sur un emplacement réseau ou à partir d’un fichier WSDL. Il génère un fichier source compatible avec .NET Core, définissant une classe de proxy WCF avec des méthodes que vous pouvez utiliser pour accéder aux opérations de service Web.

**L’outil dotnet-svcutil** est une alternative au fournisseur de services connectés [**WCF Web Service Reference**](wcf-web-service-reference-guide.md) Visual Studio, qui a d’abord été livré avec Visual Studio 2017 version 15.5. **L’outil dotnet-svcutil,** en tant qu’outil .NET, est disponible sur Linux, macOS et Windows.

## <a name="wcf-dotnet-svcutilxmlserializer-tool"></a>Outil dotnet-svcutil.xmlserializer WCF

Sur le .NET Framework, vous pouvez prégénérer un assembly de sérialisation à l’aide de l’outil svcutil. L’outil WCF [dotnet-svcutil.xmlserializer](dotnet-svcutil.xmlserializer-guide.md) fournit des fonctionnalités similaires sur .NET Core. Il prégénère un code de sérialisation C# pour les types dans l’application cliente qui sont utilisés par le contrat de service WCF et qui peuvent être sérialisés par <xref:System.Xml.Serialization.XmlSerializer>. Cela améliore les performances de démarrage de la sérialisation XML lors de la sérialisation ou de la désérialisation de ces types d’objets.

## <a name="xml-serializer-generator"></a>Générateur de sérialiseur XML

Comme le [Générateur de sérialiseur XML (sgen.exe)](../../standard/serialization/xml-serializer-generator-tool-sgen-exe.md) pour le .NET Framework, le [package NuGet Microsoft.XmlSerializer.Generator](https://www.nuget.org/packages/Microsoft.XmlSerializer.Generator) est la solution pour les bibliothèques .NET Core et .NET Standard. Il crée un assembly de sérialisation XML pour les types contenus dans un assembly afin d’améliorer les performances de démarrage de la sérialisation XML pendant la sérialisation ou la désérialisation des objets de ces types avec <xref:System.Xml.Serialization.XmlSerializer>.
