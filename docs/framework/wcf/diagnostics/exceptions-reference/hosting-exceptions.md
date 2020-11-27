---
title: Exceptions d'hébergement
ms.date: 03/30/2017
ms.assetid: ad9e14f8-fa17-4d59-b365-fe0e7ec17c98
ms.openlocfilehash: 342420f10ed53e4f4786ed9506cfde5fbfcfc957
ms.sourcegitcommit: bc293b14af795e0e999e3304dd40c0222cf2ffe4
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 11/26/2020
ms.locfileid: "96263332"
---
# <a name="hosting-exceptions"></a>Exceptions d'hébergement

Cette rubrique répertorie toutes les exceptions générées par l'hébergement.  
  
## <a name="exception-list"></a>Liste des exceptions  
  
|Code de la ressource|Chaîne de la ressource|  
|-------------------|---------------------|  
|Hosting_AddressIsAbsoluteUri|L'URI complet n'est pas autorisé. Les URI complets ne sont pas pris en compte pour l'API ServiceHostingEnvironment.EnsureServiceAvailable. Utilisez un chemin d'accès virtuel pour le service correspondant.|  
|Hosting_BuildProviderCouldNotCreateType|Le type CLR spécifié ne peut pas être chargé pendant la compilation de service. Vérifiez que ce type est défini dans un fichier source situé dans le \\ répertoire \ App_Code de l’application, contenu dans un assembly compilé situé dans le répertoire \bin de l’application \\ , ou présent dans un assembly installé dans le global assembly cache. Le nom du type respecte la casse. Les répertoires tels que \\ \ App_Code et \\ \bin doivent se trouver dans le répertoire racine de l’application. Les \\ répertoires \ App_Code et \\ \Bin ne peuvent pas être imbriqués dans des sous-répertoires.|
