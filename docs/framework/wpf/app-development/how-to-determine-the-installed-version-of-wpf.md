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
# <a name="how-to-determine-the-installed-version-of-wpf"></a><span data-ttu-id="42cc0-102">Comment :déterminer la version installée de WPF</span><span class="sxs-lookup"><span data-stu-id="42cc0-102">How to: Determine the Installed Version of WPF</span></span>
<span data-ttu-id="42cc0-103">Le numéro de version de la version actuellement installée de [!INCLUDE[TLA#tla_winclient](../../../../includes/tlasharptla-winclient-md.md)] se trouve dans le **Registre**.</span><span class="sxs-lookup"><span data-stu-id="42cc0-103">The version number for the current installed version of [!INCLUDE[TLA#tla_winclient](../../../../includes/tlasharptla-winclient-md.md)] is located in the **Registry**.</span></span>  
  
 <span data-ttu-id="42cc0-104">Pour rechercher le numéro de version :</span><span class="sxs-lookup"><span data-stu-id="42cc0-104">To find the version number:</span></span>  
  
1. <span data-ttu-id="42cc0-105">Dans le menu **Démarrer** , cliquez sur **Exécuter**.</span><span class="sxs-lookup"><span data-stu-id="42cc0-105">On the **Start** menu, click **Run**.</span></span>  
  
2. <span data-ttu-id="42cc0-106">Dans **ouvrir**, tapez **regedit. exe**.</span><span class="sxs-lookup"><span data-stu-id="42cc0-106">In **Open**, type **regedit.exe**.</span></span>  
  
3. <span data-ttu-id="42cc0-107">Ouvrez la clé suivante :</span><span class="sxs-lookup"><span data-stu-id="42cc0-107">Open the following key:</span></span>  
  
 `HKEY_LOCAL_MACHINE\SOFTWARE\Microsoft\NET Framework Setup\NDP\v3.0\Setup\Windows Presentation Foundation`  
  
 <span data-ttu-id="42cc0-108">Le numéro de version de [!INCLUDE[TLA2#tla_winclient](../../../../includes/tla2sharptla-winclient-md.md)] est stocké dans la valeur de **version** .</span><span class="sxs-lookup"><span data-stu-id="42cc0-108">The [!INCLUDE[TLA2#tla_winclient](../../../../includes/tla2sharptla-winclient-md.md)] version number is stored in the **Version** value.</span></span>
