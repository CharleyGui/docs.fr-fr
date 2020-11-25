---
title: 'NETSDK1005 et NETSDK1047 : la cible est manquante dans le fichier d’élément multimédia'
description: La résolution du problème d’un fichier de ressources n’a pas de cible.
author: sfoslund
ms.topic: error-reference
ms.date: 10/09/2020
f1_keywords:
- NETSDK1005
- NETSDK1047
ms.openlocfilehash: 207c8b0274c13e7af594e05cfac2a95907f85b81
ms.sourcegitcommit: d8020797a6657d0fbbdff362b80300815f682f94
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 11/24/2020
ms.locfileid: "95717901"
---
# <a name="netsdk1005-and-netsdk1047-asset-file-is-missing-target"></a>NETSDK1005 et NETSDK1047 : la cible est manquante dans le fichier d’élément multimédia

**Cet article s’applique à :** ✔️ Kit de développement logiciel (SDK) 2.1.100 .net Core et versions ultérieures

Lorsque le kit de développement logiciel (SDK) .NET émet une erreur NETSDK1005 ou NETSDK1047, le fichier de ressources du projet ne contient pas d’informations sur l’un de vos frameworks cibles. Ce problème peut généralement être résolu en s’assurant que la restauration est exécutée et que la valeur cible manquante est incluse dans la `TargetFrameworks` propriété de votre projet.

> [!NOTE]
> Il y avait un problème connu avec les premières versions de .NET 5 Preview 8 lorsqu’il était utilisé avec les versions de Visual Studio 16,8 préliminaires qui ont provoqué cette erreur. Plus précisément, si la cible manquante est `net5.0-windows7.0` ou `net5.0` , assurez-vous que vous avez mis à jour vers les dernières versions de Visual Studio et du kit de développement logiciel (SDK) .net 5.
