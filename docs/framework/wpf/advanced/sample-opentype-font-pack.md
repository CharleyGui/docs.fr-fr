---
title: Exemple de pack de polices OpenType
ms.date: 03/30/2017
helpviewer_keywords:
- OpenType font pack [WPF]
- fonts [WPF], OpenType font pack
- typography [WPF], OpenType font pack
ms.assetid: 56b46fa1-a44e-419b-8f14-25ad51c715c3
ms.openlocfilehash: be9bc6e0cddc0581b9acb319f7d1fc1c81dae268
ms.sourcegitcommit: 011314e0c8eb4cf4a11d92078f58176c8c3efd2d
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 02/09/2020
ms.locfileid: "77095110"
---
# <a name="sample-opentype-font-pack"></a>Exemple de pack de polices OpenType
Cette rubrique fournit une vue d’ensemble des exemples de polices OpenType distribuées avec l’SDK Windows. Les exemples de polices prennent en charge les fonctionnalités OpenType étendues qui peuvent être utilisées par les applications [!INCLUDE[TLA#tla_winclient](../../../../includes/tlasharptla-winclient-md.md)].  

<a name="overview"></a>   
## <a name="fonts-in-the-opentype-font-pack"></a>Polices du pack de polices OpenType  
 L’SDK Windows fournit un ensemble d’exemples de polices OpenType que vous pouvez utiliser pour créer des applications [!INCLUDE[TLA#tla_winclient](../../../../includes/tlasharptla-winclient-md.md)]. Les exemples de polices sont fournis sous licence Ascender Corporation. Ces polices implémentent uniquement un sous-ensemble des fonctionnalités définies par le format OpenType. Le tableau suivant répertorie les noms des exemples de polices OpenType.  
  
|**Nom**|**File**|  
|--------------|--------------|  
|Kootenay|Kooten.ttf|  
|Lindsey|Linds.ttf|  
|Miramonte|Miramo.ttf|  
|Miramonte Bold|Miramob.ttf|  
|Pericles|Peric.ttf|  
|Pericles Light|Pericl.ttf|  
|Pescadero|Pesca.ttf|  
|Pescadero Bold|Pescab.ttf|  
  
 L’illustration suivante montre à quoi ressemblent les exemples de polices OpenType.  
  
 ![Liste des noms de police de l'exemple de pack de polices](./media/sample-opentype-font-pack/font-names-sample-pack.gif)  
  
 Les exemples de polices sont fournis sous licence Ascender Corporation. Ascender est un fournisseur de polices avancées. Pour obtenir une licence des versions étendues ou personnalisées des exemples de polices, consultez le [site web d’Ascender Corporation](https://www.monotype.com/).  
  
> [!NOTE]
> En tant que développeur, vous devez vérifier que vous disposez des droits de licence nécessaires pour toute police incorporée dans une application ou redistribuée.  
  
<a name="installing_the_fonts"></a>   
## <a name="installing-the-fonts"></a>Installation des polices  
 Vous avez la possibilité d’installer les exemples de polices OpenType dans le répertoire des polices Windows par défaut, **\Windows\Fonts**. Utilisez le panneau de configuration des polices pour installer les polices. Une fois ces polices sur votre ordinateur, elles sont accessibles à toutes les applications qui référencent les polices Windows par défaut. Pour afficher un jeu de caractères représentatif dans plusieurs tailles de police, double-cliquez sur le fichier de police. La capture d’écran suivante montre le fichier de police Lindsey, Linds.ttf.  
  
 ![Police Lindsey (OpenType)](./media/typographyinwpf-04.png "TypographyInWPF_04")  
Affichage de la police Lindsey  
  
<a name="using_the_fonts"></a>   
## <a name="using-the-fonts"></a>Utilisation des polices  
 Vous pouvez utiliser des polices dans votre application de deux manières. Vous pouvez ajouter des polices à votre application sous forme d’éléments de contenu de projet qui ne sont pas incorporés comme des ressources d’assembly. Vous pouvez également ajouter des polices à votre application sous forme d’éléments de ressource de projet incorporés qui sont incorporés dans les fichiers d’assembly de l’application. Pour plus d’informations, consultez [Empaquetage de polices avec des applications](packaging-fonts-with-applications.md).  
  
## <a name="see-also"></a>Voir aussi

- <xref:System.Windows.Documents.Typography>
- [Fonctionnalités des polices OpenType](opentype-font-features.md)
- [Empaquetage de polices avec des applications](packaging-fonts-with-applications.md)
