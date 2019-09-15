---
title: 'Procédure : afficher un contrôle dans la boîte de dialogue Choisir des éléments de boîte à outils'
ms.date: 08/23/2019
helpviewer_keywords:
- global assembly cache [Windows Forms], Choose Toolbox Items dialog box
- AssemblyFoldersEx [Windows Forms], Choose Toolbox Items dialog box
- controls [Windows Forms], display in Choose Toolbox Items dialog box
- assembly folder registration [Windows Forms], Choose Toolbox Items dialog box
- Choose Toolbox Items dialog box [Windows Forms], display control
ms.assetid: 01ef6eba-d044-40f0-951d-78eff7ebd9a9
author: gewarren
ms.author: gewarren
manager: jillfra
ms.openlocfilehash: f52c1d127df8f0e831db0749e3453bb1c54d5886
ms.sourcegitcommit: 7b1ce327e8c84f115f007be4728d29a89efe11ef
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 09/13/2019
ms.locfileid: "70972069"
---
# <a name="how-to-display-a-control-in-the-choose-toolbox-items-dialog-box"></a>Procédure : afficher un contrôle dans la boîte de dialogue Choisir des éléments de boîte à outils

Lorsque vous développez et distribuez des contrôles, vous souhaiterez peut-être que ces contrôles s’affichent dans la boîte de dialogue **choisir des éléments de boîte à outils** de Visual Studio, qui s’affiche lorsque vous cliquez avec le bouton droit sur la boîte **à outils** et sélectionnez **choisir les éléments**. Vous pouvez activer votre contrôle pour qu’il s’affiche dans cette boîte de dialogue à l’aide de la procédure d’inscription AssemblyFoldersEx.

Pour afficher votre contrôle dans la boîte de dialogue choisir des éléments de boîte à outils :

- Installez votre assembly de contrôle sur le Global Assembly Cache. Pour plus d’informations, consultez [Guide pratique pour installer un assembly dans le Global Assembly Cache](../../app-domains/install-assembly-into-gac.md)

  ou

- Inscrivez votre contrôle et ses assemblys au moment du design associés à l’aide de la procédure d’inscription AssemblyFoldersEx. AssemblyFoldersEx est un emplacement du registre où les fournisseurs tiers stockent les chemins d’accès de chaque version de l’infrastructure qu’ils prennent en charge. La résolution au moment du design peut rechercher des assemblys de référence dans cet emplacement du Registre. Le script de Registre peut spécifier les contrôles que vous souhaitez voir apparaître dans la boîte à outils.

## <a name="see-also"></a>Voir aussi

- [Développement de contrôles Windows Forms au moment du design](developing-windows-forms-controls-at-design-time.md)
- [Guide pratique : installer un assembly dans le Global Assembly Cache](../../app-domains/install-assembly-into-gac.md)
- [Procédure pas à pas : Remplissage automatique de la boîte à outils avec des composants personnalisés](walkthrough-automatically-populating-the-toolbox-with-custom-components.md)
