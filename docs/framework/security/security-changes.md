---
title: Modifications de sécurité dans le .NET Framework
ms.date: 03/30/2017
helpviewer_keywords:
- Allow Partially Trusted Callers attribute
- .NET Framework 4, security changes
- .NET Framework security
- security-transparent code
- security-critical code
- code access security, changes
ms.assetid: 5e87881c-9c13-4b52-8ad1-e34bb46e8aaa
author: mairaw
ms.author: mairaw
ms.openlocfilehash: af2869e5ca3b41778c094b7a78a9493e74868811
ms.sourcegitcommit: 81ad1f09b93f3b3e6706a7f2e4ddf50ef229ea3d
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 11/20/2019
ms.locfileid: "74204504"
---
# <a name="security-changes-in-the-net-framework"></a>Modifications de sécurité dans le .NET Framework

The most important change to security in the .NET Framework 4.5 is in strong naming. Pour obtenir une description de ces modifications, consultez [Enhanced Strong Naming](../../standard/assembly/enhanced-strong-naming.md) .  
  
Le .NET Framework fournit un modèle de sécurité à deux niveaux pour les applications managées. Windows 8.x Store apps run in a Windows security container that limits access to resources. Dans ce conteneur, les applications managées s'exécutent en mode confiance totale. Du point de vue de la sécurité d'accès du code (CAS), un développeur ne peut rien faire pour élever les privilèges. Pour plus d’informations sur les privilèges octroyés par Windows, consultez [Déclarations des fonctionnalités d’application (applications du Windows Store)](https://go.microsoft.com/fwlink/?LinkId=230436) dans le centre de développement Windows. For information about creating a Windows 8.x Store app, see [Create your first Windows Store app using C# or Visual Basic](https://go.microsoft.com/fwlink/?LinkId=230461).
