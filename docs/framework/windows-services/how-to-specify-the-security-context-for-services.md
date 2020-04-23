---
title: 'Comment : spécifier le contexte de sécurité des services'
ms.date: 03/30/2017
helpviewer_keywords:
- Windows Service applications, security
- security [Visual Studio], contexts
- contexts, Visual Studio security
- security [Visual Studio], service applications
- ServiceProcessInstaller class, security context
- services, security
- ServiceInstaller class, security context
ms.assetid: 02187c7b-dbf2-45f2-96c2-e11010225a22
author: ghogen
ms.openlocfilehash: dd2a9c4485e151d4cb1c9d5ae3a95a69fcc416d4
ms.sourcegitcommit: 289e06e904b72f34ac717dbcc5074239b977e707
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 09/17/2019
ms.locfileid: "71053579"
---
# <a name="how-to-specify-the-security-context-for-services"></a>Comment : spécifier le contexte de sécurité des services
Par défaut, les services s’exécutent dans un contexte de sécurité différent de celui de l’utilisateur connecté. Les services s’exécutent dans le contexte du compte système par défaut, appelé `LocalSystem`, ce qui leur confère des privilèges d’accès aux ressources système différents de ceux de l’utilisateur. Vous pouvez changer ce comportement si vous souhaitez que votre service s’exécute sous un autre compte d’utilisateur.  
  
 Pour définir le contexte de sécurité, manipulez la propriété <xref:System.ServiceProcess.ServiceProcessInstaller.Account%2A> du processus dans lequel le service s’exécute. Cette propriété vous permet d’affecter au service l’un des quatre types de comptes suivants :  
  
- `User` : le système demande un nom d’utilisateur et un mot de passe valides quand le service est installé et s’exécute dans le contexte d’un compte spécifié par un utilisateur unique sur le réseau.  
  
- `LocalService` : s’exécute dans le contexte d’un compte qui se comporte comme un utilisateur non privilégié sur l’ordinateur local, et présente des informations d’identification anonymes à tout serveur distant.  
  
- `LocalSystem` : s’exécute dans le contexte d’un compte qui fournit des privilèges locaux étendus, et présente les informations d’identification de l’ordinateur à tout serveur distant.  
  
- `NetworkService` : s’exécute dans le contexte d’un compte qui se comporte comme un utilisateur non privilégié sur l’ordinateur local, et présente les informations d’identification de l’ordinateur à tout serveur distant.  
  
 Pour plus d’informations, consultez l’énumération <xref:System.ServiceProcess.ServiceAccount>.  
  
### <a name="to-specify-the-security-context-for-a-service"></a>Pour spécifier le contexte de sécurité d’un service  
  
1. Après avoir créé votre service, ajoutez les programmes d’installation nécessaires à celui-ci. Pour plus d’informations, consultez [Guide pratique pour ajouter des programmes d’installation à votre application de service](how-to-add-installers-to-your-service-application.md).  
  
2. Dans le concepteur, accédez à la classe `ProjectInstaller`, puis cliquez sur le programme d’installation du processus de service pour le service que vous utilisez.  
  
    > [!NOTE]
    > La classe `ProjectInstaller` comprend au moins deux composants d’installation pour chaque application de service : un qui installe les processus pour tous les services dans le projet, et un programme d’installation pour chaque service contenu dans l’application. Dans le cas présent, sélectionnez <xref:System.ServiceProcess.ServiceProcessInstaller>.  
  
3. Dans la fenêtre **Propriétés**, définissez <xref:System.ServiceProcess.ServiceProcessInstaller.Account%2A> avec la valeur appropriée.  
  
## <a name="see-also"></a>Voir aussi

- [Présentation des applications de service Windows](introduction-to-windows-service-applications.md)
- [Comment : ajouter des programmes d'installation à votre application de service](how-to-add-installers-to-your-service-application.md)
- [Guide pratique pour créer des services Windows](how-to-create-windows-services.md)
