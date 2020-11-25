---
title: 'NETSDK1073 : FrameworkReference n’a pas été reconnu'
description: Comment résoudre le problème où le FrameworkReference est introuvable.
author: marcpopMSFT
ms.topic: error-reference
ms.date: 10/9/2020
f1_keywords:
- NETSDK1073
ms.openlocfilehash: 2b2dbf2a0d3e13dca4fe634529b7951f2333ce28
ms.sourcegitcommit: d8020797a6657d0fbbdff362b80300815f682f94
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 11/24/2020
ms.locfileid: "95713026"
---
# <a name="netsdk1073-the-frameworkreference-was-not-recognized"></a>NETSDK1073 : FrameworkReference n’a pas été reconnu

**Cet article s’applique à :** ✔️ Kit de développement logiciel (SDK) 2.1.100 .net Core et versions ultérieures

Cette erreur signifie généralement qu’il existe une version d’un FrameworkReference particulier que le kit de développement logiciel (SDK) ne peut pas trouver. Essayez de supprimer vos dossiers *obj* et *bin* , puis exécutez `dotnet restore` pour retélécharger les derniers packs de ciblage.

Sinon, il peut y avoir un problème avec votre installation. Vérifiez donc que vous êtes dans les dernières versions de .NET et de Visual Studio.
