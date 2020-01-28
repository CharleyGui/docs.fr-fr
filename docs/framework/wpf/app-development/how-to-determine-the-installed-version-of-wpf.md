---
title: Déterminer la version installée de WPF
titleSuffix: ''
ms.date: 03/30/2017
helpviewer_keywords:
- version [WPF], finding
ms.assetid: 99971cef-e218-4f9f-a4c1-350332741860
ms.openlocfilehash: 8fc5c380779891b44b7c4f7f8aeb5ed119d8b768
ms.sourcegitcommit: de17a7a0a37042f0d4406f5ae5393531caeb25ba
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 01/24/2020
ms.locfileid: "76735694"
---
# <a name="how-to-determine-the-installed-version-of-wpf"></a>Comment :déterminer la version installée de WPF
Le numéro de version de la version actuellement installée de [!INCLUDE[TLA#tla_winclient](../../../../includes/tlasharptla-winclient-md.md)] se trouve dans le **Registre**.  
  
 Pour rechercher le numéro de version :  
  
1. Dans le menu **Démarrer** , cliquez sur **Exécuter**.  
  
2. Dans **ouvrir**, tapez **regedit. exe**.  
  
3. Ouvrez la clé suivante :  
  
 `HKEY_LOCAL_MACHINE\SOFTWARE\Microsoft\NET Framework Setup\NDP\v3.0\Setup\Windows Presentation Foundation`  
  
 Le numéro de version de [!INCLUDE[TLA2#tla_winclient](../../../../includes/tla2sharptla-winclient-md.md)] est stocké dans la valeur de **version** .
