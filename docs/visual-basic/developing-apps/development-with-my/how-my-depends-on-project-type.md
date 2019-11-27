---
title: Comment My dépend du type de projet
ms.date: 07/20/2015
helpviewer_keywords:
- _MYTYPE
ms.assetid: c188b38e-bd9d-4121-9983-41ea6a94d28e
ms.openlocfilehash: 975b8feb001bcab22185be0a360b0512de099b79
ms.sourcegitcommit: 17ee6605e01ef32506f8fdc686954244ba6911de
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 11/22/2019
ms.locfileid: "74330268"
---
# <a name="how-my-depends-on-project-type-visual-basic"></a>Comment My dépend du type de projet (Visual Basic)

`My` expose uniquement les objets requis par un type de projet particulier. Par exemple, l’objet `My.Forms` est disponible dans une application Windows Forms, mais n’est pas disponible dans une application console. Cette rubrique décrit les objets `My` disponibles dans différents types de projets.  
  
## <a name="my-in-windows-applications-and-web-sites"></a>My dans les applications et sites Web Windows  

 `My` expose uniquement les objets qui sont utiles dans le type de projet actuel ; elle supprime les objets qui ne sont pas applicables. Par exemple, l’image suivante montre le modèle d’objet `My` dans un projet Windows Forms.  
  
 ![Diagramme qui montre le modèle mon objet dans une application Windows Forms.](./media/how-my-depends-on-project-type/my-object-model-windows-forms.png)  
  
 Dans un projet de site Web, `My` expose des objets pertinents pour un développeur Web (tels que les objets `My.Request` et `My.Response`) tout en supprimant les objets qui ne sont pas pertinents (tels que l’objet `My.Forms`). L’illustration suivante montre le modèle d’objet `My` dans un projet de site Web :  
  
 ![Diagramme qui montre le modèle mon objet dans une application Web.](./media/how-my-depends-on-project-type/my-object-model-web.png)  
  
## <a name="project-details"></a>Détails du projet  

 Le tableau suivant indique les objets `My` sont activés par défaut pour huit types de projets : application Windows, bibliothèque de classes, application console, bibliothèque de contrôles Windows, bibliothèque de contrôles Web, service Windows, vide et site Web.  
  
 Il existe trois versions de l’objet `My.Application`, deux versions de l’objet `My.Computer` et deux versions de `My.User` objet. des informations détaillées sur ces versions sont fournies dans les notes de bas de page après le tableau.  
  
|Mon objet|Application Windows|Bibliothèque de classes|Application console|Bibliothèque de contrôles Windows|Bibliothèque de contrôles Web|Service Windows|Vide|Site web|  
|---|---|---|---|---|---|---|---|---|  
|`My.Application`|**Oui** <sup>1</sup>|**Oui** <sup>2</sup>|**Oui** <sup>3</sup>|**Oui** <sup>2</sup>|Non|**Oui** <sup>3</sup>|Non|Non|  
|`My.Computer`|**Oui** <sup>4</sup>|**Oui** <sup>4</sup>|**Oui** <sup>4</sup>|**Oui** <sup>4</sup>|**Oui** <sup>5</sup>|**Oui** <sup>4</sup>|Non|**Oui** <sup>5</sup>|  
|`My.Forms`|**Oui**|Non|Non|**Oui**|Non|Non|Non|Non|  
|`My.Log`|Non|Non|Non|Non|Non|Non|Non|**Oui**|  
|`My.Request`|Non|Non|Non|Non|Non|Non|Non|**Oui**|  
|`My.Resources`|**Oui**|**Oui**|**Oui**|**Oui**|**Oui**|**Oui**|Non|Non|  
|`My.Response`|Non|Non|Non|Non|Non|Non|Non|**Oui**|  
|`My.Settings`|**Oui**|**Oui**|**Oui**|**Oui**|**Oui**|**Oui**|Non|Non|  
|`My.User`|**Oui** <sup>6</sup>|**Oui** <sup>6</sup>|**Oui** <sup>6</sup>|**Oui** <sup>6</sup>|**Oui** <sup>7</sup>|**Oui** <sup>6</sup>|Non|**Oui** <sup>7</sup>|  
|`My.WebServices`|**Oui**|**Oui**|**Oui**|**Oui**|**Oui**|**Oui**|Non|Non|  
  
 <sup>1</sup> Windows Forms version de `My.Application`. Dérive de la version de la console (voir la remarque 3); Ajoute la prise en charge de l’interaction avec les fenêtres de l’application et fournit le modèle d’application Visual Basic.  
  
 <sup>2</sup> version de la bibliothèque de `My.Application`. Fournit les fonctionnalités de base requises par une application : fournit des membres pour l’écriture dans le journal des applications et l’accès aux informations de l’application.  
  
 <sup>3</sup> version de la Console de `My.Application`. Dérive de la version de bibliothèque (voir la remarque 2) et ajoute des membres supplémentaires pour accéder aux arguments de ligne de commande et aux informations de déploiement ClickOnce de l’application.  
  
 <sup>4</sup> version de Windows de `My.Computer`. Dérive de la version du serveur (voir remarque 5) et donne accès à des objets utiles sur un ordinateur client, tels que le clavier, l’écran et la souris.  
  
 <sup>5</sup> version du serveur de `My.Computer`. Fournit des informations de base sur l’ordinateur, telles que le nom, l’accès à l’horloge, etc.  
  
 <sup>6</sup> version de Windows de `My.User`. Cet objet est associé à l’identité actuelle du thread.  
  
 <sup>7</sup> version Web de `My.User`. Cet objet est associé à l’identité de l’utilisateur de la requête HTTP actuelle de l’application.  
  
## <a name="see-also"></a>Voir aussi

- <xref:Microsoft.VisualBasic.ApplicationServices.ApplicationBase>
- <xref:Microsoft.VisualBasic.Devices.Computer>
- <xref:Microsoft.VisualBasic.Logging.Log>
- <xref:Microsoft.VisualBasic.ApplicationServices.User>
- [Personnalisation de la disponibilité ou non des objets dans My](../../../visual-basic/developing-apps/customizing-extending-my/customizing-which-objects-are-available-in-my.md)
- [Compilation conditionnelle](../../../visual-basic/programming-guide/program-structure/conditional-compilation.md)
- [-définir (Visual Basic)](../../../visual-basic/reference/command-line-compiler/define.md)
- [My.Forms (objet)](../../../visual-basic/language-reference/objects/my-forms-object.md)
- [My.Request (objet)](../../../visual-basic/language-reference/objects/my-request-object.md)
- [My.Response (objet)](../../../visual-basic/language-reference/objects/my-response-object.md)
- [My.WebServices (objet)](../../../visual-basic/language-reference/objects/my-webservices-object.md)
