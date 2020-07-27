---
title: Vue d'ensemble de la sécurité UI Automation
description: Lisez une vue d’ensemble du modèle de sécurité pour Microsoft UI Automation. Comprendre le contrôle de compte d’utilisateur, les tâches qui requièrent des privilèges plus élevés et les fichiers manifestes.
ms.date: 03/30/2017
helpviewer_keywords:
- UI Automation, security model
- security model, UI Automation
ms.assetid: 1d853695-973c-48ae-b382-4132ae702805
ms.openlocfilehash: d483f282db8ce8e5653d6d83361fa44df05f63f5
ms.sourcegitcommit: 87cfeb69226fef01acb17c56c86f978f4f4a13db
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 07/24/2020
ms.locfileid: "87163143"
---
# <a name="ui-automation-security-overview"></a>Vue d'ensemble de la sécurité UI Automation

> [!NOTE]
> Cette documentation s'adresse aux développeurs .NET Framework qui souhaitent utiliser les classes [!INCLUDE[TLA2#tla_uiautomation](../../../includes/tla2sharptla-uiautomation-md.md)] managées définies dans l'espace de noms <xref:System.Windows.Automation>. Pour obtenir les dernières informations sur [!INCLUDE[TLA2#tla_uiautomation](../../../includes/tla2sharptla-uiautomation-md.md)], consultez [API Windows Automation : UI Automation](/windows/win32/winauto/entry-uiauto-win32).

Cette vue d’ensemble décrit le modèle de sécurité de [!INCLUDE[TLA#tla_uiautomation](../../../includes/tlasharptla-uiautomation-md.md)] dans Windows Vista.

<a name="User_Account_Control"></a>

## <a name="user-account-control"></a>Contrôle de compte d'utilisateur

La sécurité est un objectif majeur de Windows Vista et, parmi les innovations, c’est la possibilité pour les utilisateurs de s’exécuter en tant qu’utilisateurs standard (non-administrateur) sans qu’il soit nécessaire de bloquer l’exécution d’applications et de services nécessitant des privilèges plus élevés.

Dans Windows Vista, la plupart des applications sont fournies avec un jeton d’administration ou standard. Si une application ne peut pas être identifiée en tant qu'application administrative, elle est lancée par défaut en tant qu'application standard. Avant qu’une application identifiée comme administrative puisse être lancée, Windows Vista invite l’utilisateur à donner son consentement pour exécuter l’application avec des privilèges élevés. L'invite de consentement s'affiche par défaut, même si l'utilisateur est membre du groupe Administrateurs local. Cela est dû au fait que les administrateurs sont considérés comme des utilisateurs standard jusqu'à ce qu'une application ou un composant système nécessitant des informations d'identification d'administration demande l'autorisation de s'exécuter.

<a name="Tasks_Requiring_Higher_Privileges"></a>

## <a name="tasks-requiring-higher-privileges"></a>Tâches nécessitant des privilèges plus élevés

Quand un utilisateur tente d’effectuer une tâche qui requiert des privilèges d’administrateur, Windows Vista présente une boîte de dialogue demandant à l’utilisateur de continuer. Cette boîte de dialogue bénéficie d'une protection contre les communications interprocessus, ce qui empêche les logiciels malveillants de simuler l'entrée de l'utilisateur. De même, d'autres processus ne sont normalement pas autorisés à accéder à l'écran d'ouverture de session sur le Bureau.

Les clients UI Automation doivent communiquer avec d’autres processus, certains d’entre eux pouvant être exécutés à un niveau de privilège supérieur. Les clients peuvent aussi avoir besoin d'accéder à des boîtes de dialogue système qui ne sont normalement pas visibles à d'autres processus. Par conséquent, les clients [!INCLUDE[TLA2#tla_uiautomation](../../../includes/tla2sharptla-uiautomation-md.md)] doivent être approuvés par le système et s'exécuter avec des privilèges spéciaux.

Pour avoir l'autorisation de communiquer avec des applications exécutées à un niveau de privilège plus élevé, les applications doivent être signées.

<a name="Manifest_Files"></a>

## <a name="manifest-files"></a>Fichiers manifeste

Pour accéder à l’interface utilisateur du système protégé, les applications doivent être générées avec un fichier manifeste qui comprend l' `uiAccess` attribut dans la `requestedExecutionLevel` balise, comme suit :

```xml
<trustInfo xmlns="urn:schemas-microsoft-com:asm.v3">
  <security>
    <requestedPrivileges>
      <requestedExecutionLevel
        level="highestAvailable"
        uiAccess="true" />
    </requestedPrivileges>
  </security>
</trustInfo>
```

Dans ce code, la valeur de l'attribut `level` n'est qu'un exemple.

`uiAccess`est « false » par défaut ; autrement dit, si l’attribut est omis ou s’il n’existe aucun manifeste pour l’assembly, l’application ne sera pas en mesure d’accéder à l’interface utilisateur protégée.
