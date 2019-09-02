---
title: Utilisation des domaines d'application
ms.date: 03/30/2017
helpviewer_keywords:
- application domains, about
- common language runtime, application domains
- runtime, application domains
ms.assetid: c6d99815-e022-4d2c-9420-1d7ab5b9d504
author: rpetrusha
ms.author: ronpet
ms.openlocfilehash: 5ebd1de46eb2757098a369b58dd9a6c0009e5b95
ms.sourcegitcommit: 2d792961ed48f235cf413d6031576373c3050918
ms.translationtype: HT
ms.contentlocale: fr-FR
ms.lasthandoff: 09/02/2019
ms.locfileid: "61674886"
---
# <a name="using-application-domains"></a>Utilisation des domaines d'application
Les domaines d’application fournissent une unité d’isolation pour le common language runtime. Ils sont créés et exécutés dans un processus. Les domaines d’application sont généralement créés par un hôte de runtime, qui est une application responsable du chargement du runtime dans un processus et de l’exécution du code utilisateur dans un domaine d’application. L’hôte de runtime crée un processus et un domaine d’application par défaut et exécute le code managé dans ce domaine d’application. Les hôtes de runtime comprennent ASP.NET, Microsoft Internet Explorer et le shell Windows.  
  
 Pour la plupart des applications, vous n’êtes pas obligé de créer votre propre domaine d’application ; l’hôte du runtime se charge de créer le domaine d’application dont vous avez besoin. Toutefois, vous pouvez créer et configurer des domaines d’application supplémentaires si votre application doit isoler du code ou utiliser et décharger des DLL.  
  
## <a name="in-this-section"></a>Dans cette section  
 [Guide pratique pour créer un domaine d’application](../../../docs/framework/app-domains/how-to-create-an-application-domain.md)  
 Décrit comment créer un domaine d’application par programmation.  
  
 [Guide pratique pour décharger un domaine d’application](../../../docs/framework/app-domains/how-to-unload-an-application-domain.md)  
 Décrit comment décharger un domaine d’application par programmation.  
  
 [Guide pratique pour configurer un domaine d’application](../../../docs/framework/app-domains/how-to-configure-an-application-domain.md)  
 Propose une introduction à la configuration d’un domaine d’application.  
  
 [Récupération d'informations d'installation à partir d'un domaine d'application](../../../docs/framework/app-domains/retrieve-setup-information.md)  
 Décrit comment récupérer les informations de configuration d’un domaine d’application.  
  
 [Guide pratique pour charger des assemblys dans un domaine d’application](../../../docs/framework/app-domains/how-to-load-assemblies-into-an-application-domain.md)  
 Décrit comment charger un assembly dans un domaine d’application.  
  
 [Guide pratique pour obtenir des informations relatives au type et aux membres à partir d’un assembly](../../../docs/framework/app-domains/how-to-obtain-type-and-member-information-from-an-assembly.md)  
 Décrit comment récupérer des informations sur un assembly.  
  
 [Clichés instantanés d'assemblys](../../../docs/framework/app-domains/shadow-copy-assemblies.md)  
 Décrit comment utiliser des clichés instantanés pour mettre à jour des assemblys pendant leur utilisation, et comment configurer des clichés instantanés.  
  
 [Guide pratique pour recevoir des notifications des exceptions de première chance](../../../docs/framework/app-domains/how-to-receive-first-chance-exception-notifications.md)  
 Explique comment recevoir une notification indiquant qu’une exception a été levée, avant que le common language runtime ne commence à rechercher des gestionnaires d’exceptions.  
  
 [Résoudre les chargements d'assemblys](../../../docs/framework/app-domains/resolve-assembly-loads.md)  
 Offre des conseils sur l’utilisation de l’événement <xref:System.AppDomain.AssemblyResolve?displayProperty=nameWithType> pour résoudre les échecs de chargement de l’assembly.  
  
## <a name="reference"></a>Référence  
 <xref:System.AppDomain>  
 Représente un domaine d’application. Fournit des méthodes pour la création et le contrôle des domaines d’application.  
  
## <a name="related-sections"></a>Rubriques connexes  
 [Assemblys dans le Common Language Runtime](../../../docs/framework/app-domains/assemblies-in-the-common-language-runtime.md)  
 Fournit une vue d’ensemble des fonctions exécutées par les assemblys.  
  
 [Programmation à l’aide d’assemblys](../../../docs/framework/app-domains/programming-with-assemblies.md)  
 Décrit comment créer, signer et définir des attributs sur des assemblys.  
  
 [Émission d’assemblys et de méthodes dynamiques](../../../docs/framework/reflection-and-codedom/emitting-dynamic-methods-and-assemblies.md)  
 Décrit comment créer des assemblys dynamiques.  
  
 [Domaines d’application](../../../docs/framework/app-domains/application-domains.md)  
 Fournit une vue d'ensemble conceptuelle des domaines d'application.  
  
 [Vue d’ensemble de la réflexion](../../../docs/framework/reflection-and-codedom/reflection.md)  
 Explique comment utiliser la classe **Reflection** pour obtenir des informations sur un assembly.
