---
title: Outils supplémentaires
description: Vue d’ensemble des outils supplémentaires que vous pouvez installer et qui prennent en charge et étendent les fonctionnalités .NET.
author: mlacouture
ms.date: 02/13/2020
ms.custom: mvc
ms.openlocfilehash: 243f2da1c6f7809ac710c9700ea4cbde6f289295
ms.sourcegitcommit: 68c9d9d9a97aab3b59d388914004b5474cf1dbd7
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 01/30/2021
ms.locfileid: "99216393"
---
# <a name="net-additional-tools-overview"></a>Vue d’ensemble des outils supplémentaires .NET

Cette section compile une liste d’outils qui prennent en charge et étendent les fonctionnalités .NET, en plus de l’interface CLI .NET.

## <a name="net-uninstall-tool"></a>Outil de désinstallation .NET

L' [outil de désinstallation de .net](https://github.com/dotnet/cli-lab/releases) ( `dotnet-core-uninstall` ) vous permet de nettoyer les kits de développement logiciel (SDK) et runtimes .net sur un système de sorte que seules les versions spécifiées restent. Une collection d’options est disponible pour spécifier les versions qui sont désinstallées.

## <a name="net-diagnostic-tools"></a>Outils de diagnostic .NET

[dotnet-Counters](../diagnostics/dotnet-counters.md) est un outil d’analyse des performances pour l’analyse de l’intégrité et des performances de premier niveau.

[dotnet-dump](../diagnostics/dotnet-dump.md) offre un moyen de collecter et d’analyser les vidages principaux Windows et Linux sans débogueur natif.

[dotnet-gcdump](../diagnostics/dotnet-gcdump.md) fournit un moyen de collecter les vidages de mémoire (garbage collector) des processus .net en direct.

[dotnet-trace](../diagnostics/dotnet-trace.md) collecte les données de profilage de votre application qui peuvent vous aider dans des scénarios où vous devez déterminer ce qui entraîne l’exécution lente d’une application.

## <a name="net-install-tool-for-extension-authors"></a>Outil d’installation .NET pour les auteurs d’extensions

L' [outil d’installation de .net pour les auteurs d’extensions](https://github.com/dotnet/vscode-dotnet-runtime) est une extension de Visual Studio code qui permet d’acquérir le Runtime .net spécifiquement pour les auteurs d’extensions vs code. Cet outil est conçu pour être utilisé dans les extensions écrites en .NET et nécessiter .NET pour démarrer des éléments de l’extension (par exemple, un serveur de langage). L’extension n’est pas destinée à être utilisée directement par les utilisateurs pour installer .NET en vue du développement.

## <a name="wcf-web-service-reference-tool"></a>Outil de référence de service Web WCF

L’outil de référence de [service Web](wcf-web-service-reference-guide.md) WCF (Windows Communication Foundation) est un fournisseur de services connectés Visual Studio qui a fait ses débuts dans [Visual studio 2017 version 15,5](/visualstudio/releasenotes/vs2017-relnotes-v15.5#WCFTools). Cet outil récupère les métadonnées d’un service Web dans la solution actuelle, sur un emplacement réseau ou à partir d’un fichier WSDL. Il génère un fichier source compatible avec .NET, définissant une classe proxy WCF avec des méthodes que vous pouvez utiliser pour accéder aux opérations de service Web.

## <a name="wcf-dotnet-svcutil-tool"></a>Outil dotnet-svcutil WCF

L' [outil WCF dotnet-Svcutil](dotnet-svcutil-guide.md) est un outil .net qui récupère les métadonnées d’un service Web sur un emplacement réseau ou à partir d’un fichier WSDL. Il génère un fichier source compatible avec .NET, définissant une classe proxy WCF avec des méthodes que vous pouvez utiliser pour accéder aux opérations de service Web.

L’outil **dotnet-Svcutil** est une alternative à la [**Référence du service Web WCF**](wcf-web-service-reference-guide.md) du fournisseur de services connectés Visual Studio, qui a été livré avec visual studio 2017 version 15,5. L’outil **dotnet-Svcutil** , en tant qu’outil .net, est disponible sur Linux, MacOS et Windows.

## <a name="wcf-dotnet-svcutilxmlserializer-tool"></a>Outil dotnet-svcutil.xmlserializer WCF

Sur le .NET Framework, vous pouvez prégénérer un assembly de sérialisation à l’aide de l’outil svcutil. L' [ outil WCFdotnet-svcutil.xmlserializer](dotnet-svcutil.xmlserializer-guide.md) offre des fonctionnalités similaires sur .net 5 (et .net Core) et les versions ultérieures. Il prégénère un code de sérialisation C# pour les types dans l’application cliente qui sont utilisés par le contrat de service WCF et qui peuvent être sérialisés par <xref:System.Xml.Serialization.XmlSerializer>. Cela améliore les performances de démarrage de la sérialisation XML lors de la sérialisation ou de la désérialisation de ces types d’objets.

## <a name="xml-serializer-generator"></a>Générateur de sérialiseur XML

À l’instar de [XML Serializer Generator (sgen.exe)](../../standard/serialization/xml-serializer-generator-tool-sgen-exe.md) pour l' .NET Framework, le [ package NuGetMicrosoft.Xmlserializer. Generator](https://www.nuget.org/packages/Microsoft.XmlSerializer.Generator) est la solution pour les bibliothèques qui ciblent .NET 5 (et .net Core) et versions ultérieures. Il crée un assembly de sérialisation XML pour les types contenus dans un assembly afin d’améliorer les performances de démarrage de la sérialisation XML pendant la sérialisation ou la désérialisation des objets de ces types avec <xref:System.Xml.Serialization.XmlSerializer>.

## <a name="generating-self-signed-certificates"></a>Génération de certificats de Self-Signed

Vous pouvez utiliser [dotnet dev-certs](self-signed-certificates-guide.md) pour créer des certificats auto-signés pour les scénarios de développement et de test.
