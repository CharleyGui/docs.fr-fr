---
title: Déploiement d'un projet de bibliothèque WCF
ms.date: 03/30/2017
ms.assetid: 9f9222fe-d358-443c-9a49-12c5498e35e7
ms.openlocfilehash: 0f4c880bbd5c1bb819a04f42e91f531250c4f32e
ms.sourcegitcommit: 27a15a55019f6b5f2733961738babe94aec0def3
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 09/15/2020
ms.locfileid: "90554317"
---
# <a name="deploying-a-wcf-library-project"></a>Déploiement d'un projet de bibliothèque WCF
Cette rubrique décrit comment vous pouvez déployer un projet de bibliothèque de services Windows Communication Foundation (WCF).  
  
## <a name="deploying-a-wcf-service-library"></a>Déploiement d'une bibliothèque du service WCF  
 Une bibliothèque de services WCF est une bibliothèque de liens dynamiques (DLL). À ce titre, elle ne peut pas être exécutée seule. Elle doit être déployée dans un environnement d'hébergement. Pour plus d’informations sur ce processus, consultez [hébergement et utilisation des services WCF](/previous-versions/dotnet/articles/bb332338(v=msdn.10)).  
  
 Une bibliothèque de service WCF peut être déployée comme tout autre service WCF. Toutefois, sachez que .NET Framework ne prend pas en charge la configuration des dll. <xref:System.Configuration> prend en charge un fichier de configuration par domaine d'application. Le projet de bibliothèque de service WCF atténue cette limitation en fournissant un fichier App.config pour la bibliothèque pendant le développement. Toutefois, le fichier App.config n'est pas reconnu après le déploiement.  
  
 Vous devez placer votre code de configuration dans le fichier de configuration reconnu par votre environnement d'hébergement. Pour l'auto-hébergement, vous devez copier le contenu du fichier App.config dans le fichier App.config de l'exécutable d'hébergement. Si vous utilisez IIS pour héberger votre service, vous devez copier le contenu du fichier App.config dans le fichier Web.config du répertoire virtuel.
