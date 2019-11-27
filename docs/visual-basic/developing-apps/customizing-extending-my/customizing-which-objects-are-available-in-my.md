---
title: Personnalisation de la disponibilité ou non des objets dans My
ms.date: 07/20/2015
helpviewer_keywords:
- My namespace [Visual Basic], customizing
- My namespace
ms.assetid: 4e8279c2-ed5b-4681-8903-8a6671874000
ms.openlocfilehash: 0387aca08e3a31b0a2045369919894d88caf5b76
ms.sourcegitcommit: 17ee6605e01ef32506f8fdc686954244ba6911de
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 11/22/2019
ms.locfileid: "74330330"
---
# <a name="customizing-which-objects-are-available-in-my-visual-basic"></a>Personnalisation de la disponibilité ou non des objets dans My (Visual Basic)

Cette rubrique décrit comment vous pouvez contrôler les `My` objets qui sont activés en définissant la constante de compilation conditionnelle `_MYTYPE` de votre projet. L’environnement de développement intégré (IDE) de Visual Studio conserve la `_MYTYPE` constante de compilation conditionnelle d’un projet synchronisée avec le type du projet.  
  
## <a name="predefined-_mytype-values"></a>Valeurs \_MYTYPE prédéfinies  

Vous devez utiliser l’option du compilateur `/define` pour définir la `_MYTYPE` constante de compilation conditionnelle. Lorsque vous spécifiez votre propre valeur pour la constante `_MYTYPE`, vous devez placer la valeur de chaîne dans des séquences de barres obliques inverses (\\"). Par exemple, vous pouvez utiliser :  
  
```console  
/define:_MYTYPE=\"WindowsForms\"  
```  
  
 Ce tableau montre ce que la `_MYTYPE` constante de compilation conditionnelle est définie sur pour plusieurs types de projets.  
  
|Type de projet|\_valeur MYTYPE|  
|------------------|--------------------|  
|Bibliothèque de classes|Windows|  
|Application console|Console|  
|Web|Internet|  
|Bibliothèque de contrôles Web|WebControl|  
|Application Windows|"WindowsForms"|  
|Application Windows, lors du démarrage avec un `Sub Main` personnalisé|"WindowsFormsWithCustomSubMain"|  
|Bibliothèque de contrôles Windows|Windows|  
|Service Windows|Console|  
|Vide|Vidé|  
  
> [!NOTE]
> Toutes les comparaisons de chaînes de compilation conditionnelle respectent la casse, quelle que soit la façon dont l’instruction `Option Compare` est définie.  
  
## <a name="dependent-_my-compilation-constants"></a>Dépendants \_mes constantes de compilation  

La `_MYTYPE` constante de compilation conditionnelle, à son tour, contrôle les valeurs de plusieurs autres `_MY` constantes de compilation :  
  
|\_MYTYPE|\_MYAPPLICATIONTYPE|\_MYCOMPUTERTYPE|\_MYFORMS|\_MYUSERTYPE|\_MYWEBSERVICES|  
|--------------|-------------------------|----------------------|---------------|------------------|---------------------|  
|Console|Console|Windows|Non défini(e)|Windows|TRUE|  
|Propre|Non défini(e)|Non défini(e)|Non défini(e)|Non défini(e)|Non défini(e)|  
|Vidé|Non défini(e)|Non défini(e)|Non défini(e)|Non défini(e)|Non défini(e)|  
|Internet|Non défini(e)|Internet|FALSE|Internet|FALSE|  
|WebControl|Non défini(e)|Internet|FALSE|Internet|TRUE|  
|« Windows » ou «»|Windows|Windows|Non défini(e)|Windows|TRUE|  
|"WindowsForms"|"WindowsForms"|Windows|TRUE|Windows|TRUE|  
|"WindowsFormsWithCustomSubMain"|Console|Windows|TRUE|Windows|TRUE|  
  
 Par défaut, les constantes de compilation conditionnelle non définies sont résolues en `FALSE`. Vous pouvez spécifier des valeurs pour les constantes non définies lors de la compilation de votre projet pour remplacer le comportement par défaut.  
  
> [!NOTE]
> Lorsque `_MYTYPE` a la valeur « Custom », le projet contient l’espace de noms `My`, mais il ne contient aucun objet. Toutefois, la définition de `_MYTYPE` sur « Empty » empêche le compilateur d’ajouter l’espace de noms `My` et ses objets.  
  
 Ce tableau décrit les effets des valeurs prédéfinies des constantes de compilation de `_MY`.  
  
|Constante|Signification|  
|--------------|-------------|  
|`_MYAPPLICATIONTYPE`|Active `My.Application`, si la constante est « console », « Windows » ou « WindowsForms » :<br /><br /> -La version « console » dérive de <xref:Microsoft.VisualBasic.ApplicationServices.ConsoleApplicationBase>. et contient moins de membres que la version « Windows ».<br />-La version « Windows » dérive de <xref:Microsoft.VisualBasic.ApplicationServices.ApplicationBase>et a moins de membres que la version « WindowsForms ».<br />-La version « WindowsForms » de `My.Application` dérive de <xref:Microsoft.VisualBasic.ApplicationServices.WindowsFormsApplicationBase>. Si la constante `TARGET` est définie sur « winexe », la classe comprend une méthode `Sub Main`.|  
|`_MYCOMPUTERTYPE`|Active `My.Computer`, si la constante est « Web » ou « Windows » :<br /><br /> -La version « Web » dérive de <xref:Microsoft.VisualBasic.Devices.ServerComputer>et a moins de membres que la version « Windows ».<br />-La version « Windows » de `My.Computer` dérive de <xref:Microsoft.VisualBasic.Devices.Computer>.|  
|`_MYFORMS`|Active `My.Forms`, si la constante est `TRUE`.|  
|`_MYUSERTYPE`|Active `My.User`, si la constante est « Web » ou « Windows » :<br /><br /> -La version « Web » de `My.User` est associée à l’identité de l’utilisateur de la requête HTTP actuelle.<br />-La version « Windows » de `My.User` est associée au principal actuel du thread.|  
|`_MYWEBSERVICES`|Active `My.WebServices`, si la constante est `TRUE`.|  
|`_MYTYPE`|Active `My.Log`, `My.Request`et `My.Response`, si la constante est « Web ».|  
  
## <a name="see-also"></a>Voir aussi

- <xref:Microsoft.VisualBasic.ApplicationServices.ApplicationBase>
- <xref:Microsoft.VisualBasic.Devices.Computer>
- <xref:Microsoft.VisualBasic.Logging.Log>
- <xref:Microsoft.VisualBasic.ApplicationServices.User>
- [Comment My dépend du type de projet](../../../visual-basic/developing-apps/development-with-my/how-my-depends-on-project-type.md)
- [Compilation conditionnelle](../../../visual-basic/programming-guide/program-structure/conditional-compilation.md)
- [-définir (Visual Basic)](../../../visual-basic/reference/command-line-compiler/define.md)
- [My.Forms (objet)](../../../visual-basic/language-reference/objects/my-forms-object.md)
- [My.Request (objet)](../../../visual-basic/language-reference/objects/my-request-object.md)
- [My.Response (objet)](../../../visual-basic/language-reference/objects/my-response-object.md)
- [My.WebServices (objet)](../../../visual-basic/language-reference/objects/my-webservices-object.md)
