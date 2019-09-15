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
ms.openlocfilehash: bfc48d4fed127b288353f0295f2de1ca33e0a8fe
ms.sourcegitcommit: 7b1ce327e8c84f115f007be4728d29a89efe11ef
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 09/13/2019
ms.locfileid: "70971214"
---
# <a name="security-changes-in-the-net-framework"></a>Modifications de sécurité dans le .NET Framework
La modification la plus importante de la sécurité dans le .NET Framework 4,5 est l’attribution d’un nom fort. Pour obtenir une description de ces modifications, consultez [Enhanced Strong Naming](../../standard/assembly/enhanced-strong-naming.md) .  
  
 Le .NET Framework fournit un modèle de sécurité à deux niveaux pour les applications managées. Les applications[!INCLUDE[win8_appname_long](../../../includes/win8-appname-long-md.md)] s'exécutent dans un conteneur de sécurité Windows qui limite l'accès aux ressources. Dans ce conteneur, les applications managées s'exécutent en mode confiance totale. Du point de vue de la sécurité d'accès du code (CAS), un développeur ne peut rien faire pour élever les privilèges. Pour plus d’informations sur les privilèges octroyés par Windows, consultez [Déclarations des fonctionnalités d’application (applications du Windows Store)](https://go.microsoft.com/fwlink/?LinkId=230436) dans le centre de développement Windows. Pour plus d’informations sur la création d’une application [!INCLUDE[win8_appname_long](../../../includes/win8-appname-long-md.md)] , consultez [Créer votre première application Windows Runtime en C# ou Visual Basic](https://go.microsoft.com/fwlink/?LinkId=230461).
