---
title: Outils et diagnostics dans .NET
author: IEvangelist
description: En savoir plus sur les outils de développement et de diagnostic disponibles pour les développeurs .NET.
ms.author: dapine
ms.date: 10/21/2020
ms.topic: overview
ms.openlocfilehash: 07c1a161a0bb429403db6852fe77749d83c19ec0
ms.sourcegitcommit: 98d20cb038669dca4a195eb39af37d22ea9d008e
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 10/22/2020
ms.locfileid: "96588389"
---
# <a name="tools-and-diagnostics-in-net"></a>Outils et diagnostics dans .NET

Dans cet article, vous découvrirez les différents outils disponibles pour les développeurs .NET. Avec .NET, vous disposez d’un kit de développement logiciel (SDK) robuste qui comprend une interface de ligne de commande (CLI). L’interface CLI .NET active la plupart des fonctionnalités tout au long du. Environnements de développement intégrés (IDE) prêts pour le NET. Cet article fournit également des ressources pour des fonctionnalités de productivité, telles que des outils CLI .NET pour diagnostiquer les problèmes de performances, les fuites de mémoire, l’UC élevée, les blocages et la prise en charge des outils pour l’analyse du code.

## <a name="net-sdk"></a>Kit de développement logiciel (SDK) .NET

Le kit de développement logiciel (SDK) .NET comprend à la fois le Runtime .NET et l’interface CLI .NET. Vous pouvez télécharger le [Kit de développement logiciel (SDK) .net](https://dotnet.microsoft.com/download) pour Windows, Linux, MacOS ou docker. Pour plus d’informations, consultez [vue d’ensemble du SDK .net](../core/sdk.md).

## <a name="net-cli"></a>CLI .NET

L’interface CLI .NET est un chaîne d’outils multiplateforme pour le développement, la génération, l’exécution et la publication d’applications .NET. L’interface CLI .NET est incluse avec le kit de développement logiciel (SDK) .NET. Pour plus d’informations, consultez [vue d’ensemble de l’interface CLI .net](../core/tools/index.md).

## <a name="ides"></a>IDE

Vous pouvez écrire des applications .NET dans [Visual Studio code](https://code.visualstudio.com/docs), [Visual Studio](/visualstudio/windows)ou [Visual Studio pour Mac](/visualstudio/mac). Pour plus d’informations sur les environnements de développement basés sur le Cloud, consultez [Visual Studio Codespaces](/visualstudio/codespaces/overview/what-is-vsonline).

## <a name="additional-tools"></a>Outils supplémentaires

En plus des outils les plus courants, .NET fournit également des outils pour des scénarios spécifiques. Certains cas d’utilisation incluent la désinstallation du kit de développement logiciel (SDK) .NET ou du Runtime .NET, la récupération de métadonnées Windows Communication Foundation (WCF), la génération de code source de proxy et la sérialisation de code XML. Pour plus d’informations, consultez la page [vue d’ensemble des outils supplémentaires .net](../core/additional-tools/index.md).

## <a name="diagnostics-and-instrumentation"></a>Diagnostics et instrumentation

En tant que développeur .NET, vous pouvez utiliser les outils de diagnostic des performances courants pour surveiller les performances des applications, profiler les applications avec le suivi, collecter les métriques de performances et analyser les fichiers de vidage. Vous pouvez collecter des mesures de performances avec des compteurs d’événements et utiliser les outils de profilage pour obtenir des informations sur la façon dont les applications s’exécutent. Pour plus d’informations, consultez [outils de diagnostic .net](../core/diagnostics/index.md).

## <a name="code-analysis"></a>Analyse du code

Les analyseurs Roslyn (.NET Compiler Platform) inspectent votre code C# ou Visual Basic pour la qualité du code et les problèmes de style de code. Pour plus d’informations, consultez [vue d’ensemble de l’analyse du code source .net](code-analysis/overview.md).
