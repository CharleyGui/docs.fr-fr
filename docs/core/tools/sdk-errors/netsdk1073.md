---
title: 'NETSDK1073 : FrameworkReference n’a pas été reconnu'
description: Comment résoudre le problème où le FrameworkReference est introuvable.
author: marcpopMSFT
ms.topic: error-reference
ms.date: 10/9/2020
f1_keywords:
- NETSDK1073
ms.openlocfilehash: 59b5f63dcfe0115feabc2d87d24a09c6a650cc62
ms.sourcegitcommit: b59237ca4ec763969a0dd775a3f8f39f8c59fe24
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 10/12/2020
ms.locfileid: "91957146"
---
# <a name="netsdk1073-the-frameworkreference-was-not-recognized"></a>NETSDK1073 : FrameworkReference n’a pas été reconnu

**Cet article s’applique à : ✔️ le kit de** développement logiciel (SDK) .NET 2.1.100 et versions ultérieures

Cette erreur signifie généralement qu’il existe une version d’un FrameworkReference particulier que le kit de développement logiciel (SDK) ne peut pas trouver. Essayez de supprimer vos dossiers *obj* et *bin* , puis exécutez `dotnet restore` pour retélécharger les derniers packs de ciblage.

Sinon, il peut y avoir un problème avec votre installation. Vérifiez donc que vous êtes dans les dernières versions de .NET et de Visual Studio.
