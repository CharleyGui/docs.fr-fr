---
title: 'Procédure : configurer un domaine d’application'
ms.date: 03/30/2017
dev_langs:
- csharp
- vb
- cpp
helpviewer_keywords:
- application domains, configuring
- ApplicationBase property
ms.assetid: 07ea8438-7a34-49f0-a7e8-3d6ff7e4a482
author: rpetrusha
ms.author: ronpet
ms.openlocfilehash: 06883646982aa6bd642dc4fce7881a289dad5901
ms.sourcegitcommit: 289e06e904b72f34ac717dbcc5074239b977e707
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 09/17/2019
ms.locfileid: "71053192"
---
# <a name="how-to-configure-an-application-domain"></a>Procédure : configurer un domaine d’application
Vous pouvez fournir au Common Language Runtime des informations de configuration pour un nouveau domaine d’application à l’aide de la classe <xref:System.AppDomainSetup>. Quand vous créez vos propres domaines d’application, la propriété la plus importante est <xref:System.AppDomainSetup.ApplicationBase%2A>. Les autres propriétés **AppDomainSetup** sont utilisées principalement par les hôtes du runtime pour configurer un domaine d’application particulier.  
  
 La propriété **ApplicationBase** définit le répertoire racine de l’application. Quand le runtime a besoin de satisfaire une demande de type, il interroge l’assembly contenant le type dans le répertoire spécifié par la propriété **ApplicationBase**.  
  
> [!NOTE]
> Un nouveau domaine d’application hérite uniquement de la propriété **ApplicationBase** du créateur.  
  
 L’exemple suivant crée une instance de la classe **AppDomainSetup**, utilise cette classe pour créer un domaine d’application, écrit les informations dans la console, puis décharge le domaine d’application.  
  
## <a name="example"></a>Exemple  
 [!code-cpp[ADApplicationBase#2](../../../samples/snippets/cpp/VS_Snippets_CLR/ADApplicationBase/CPP/source2.cpp#2)]
 [!code-csharp[ADApplicationBase#2](../../../samples/snippets/csharp/VS_Snippets_CLR/ADApplicationBase/CS/source2.cs#2)]
 [!code-vb[ADApplicationBase#2](../../../samples/snippets/visualbasic/VS_Snippets_CLR/ADApplicationBase/VB/source2.vb#2)]  
  
## <a name="see-also"></a>Voir aussi

- [Programmation avec des domaines d’application](application-domains.md#programming-with-application-domains)
- [Utilisation des domaines d’application](use.md)
