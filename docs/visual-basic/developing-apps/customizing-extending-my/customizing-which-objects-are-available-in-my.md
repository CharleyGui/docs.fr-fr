---
title: Personnalisation de la disponibilité ou non des objets dans My
ms.date: 07/20/2015
helpviewer_keywords:
- My namespace [Visual Basic], customizing
- My namespace
ms.assetid: 4e8279c2-ed5b-4681-8903-8a6671874000
ms.openlocfilehash: 5245c129281bc8c7c1c6fe9215a221889380a901
ms.sourcegitcommit: f8c270376ed905f6a8896ce0fe25b4f4b38ff498
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 06/04/2020
ms.locfileid: "84410216"
---
# <a name="customizing-which-objects-are-available-in-my-visual-basic"></a>Personnalisation de la disponibilité ou non des objets dans My (Visual Basic)

Cette rubrique décrit comment vous pouvez contrôler les `My` objets qui sont activés en définissant la constante de compilation conditionnelle de votre projet `_MYTYPE` . L’environnement de développement intégré (IDE) de Visual Studio permet de `_MYTYPE` synchroniser la constante de compilation conditionnelle d’un projet avec le type du projet.  
  
## <a name="predefined-_mytype-values"></a>Valeurs MYTYPE prédéfinies \_  

Vous devez utiliser l' `/define` option du compilateur pour définir la `_MYTYPE` constante de compilation conditionnelle. Lorsque vous spécifiez votre propre valeur pour la `_MYTYPE` constante, vous devez placer la valeur de chaîne dans des séquences de barres obliques inverses ( \\ "). Par exemple, vous pouvez utiliser :  
  
```console  
/define:_MYTYPE=\"WindowsForms\"  
```  
  
 Ce tableau montre la valeur de la `_MYTYPE` constante de compilation conditionnelle pour plusieurs types de projets.  
  
|Type de projet|\_Valeur MYTYPE|  
|------------------|--------------------|  
|Bibliothèque de classes|« Windows »|  
|Application console|Console|  
|Web|Internet|  
|Bibliothèque de contrôles Web|WebControl|  
|Application Windows|WindowsForms|  
|Application Windows, lors du démarrage avec un personnalisé`Sub Main`|"WindowsFormsWithCustomSubMain"|  
|Bibliothèque de contrôles Windows|« Windows »|  
|Service Windows|Console|  
|Vide|Vidé|  
  
> [!NOTE]
> Toutes les comparaisons de chaînes de compilation conditionnelle respectent la casse, quelle que soit la façon dont l' `Option Compare` instruction est définie.  
  
## <a name="dependent-_my-compilation-constants"></a>Dépendants \_ mes constantes de compilation  

La `_MYTYPE` constante de compilation conditionnelle, à son tour, contrôle les valeurs de plusieurs autres `_MY` constantes de compilation :  
  
|\_MYTYPE|\_MYAPPLICATIONTYPE|\_MYCOMPUTERTYPE|\_MYFORMS|\_MYUSERTYPE|\_MYWEBSERVICES|  
|--------------|-------------------------|----------------------|---------------|------------------|---------------------|  
|Console|Console|« Windows »|Indéfini|« Windows »|VRAI|  
|Propre|Indéfini|Indéfini|Indéfini|Indéfini|Indéfini|  
|Vidé|Indéfini|Indéfini|Indéfini|Indéfini|Indéfini|  
|Internet|Indéfini|Internet|FAUX|Internet|FAUX|  
|WebControl|Indéfini|Internet|FAUX|Internet|VRAI|  
|« Windows » ou «»|« Windows »|« Windows »|Indéfini|« Windows »|VRAI|  
|WindowsForms|WindowsForms|« Windows »|VRAI|« Windows »|VRAI|  
|"WindowsFormsWithCustomSubMain"|Console|« Windows »|VRAI|« Windows »|VRAI|  
  
 Par défaut, les constantes de compilation conditionnelle non définies sont résolues en `FALSE` . Vous pouvez spécifier des valeurs pour les constantes non définies lors de la compilation de votre projet pour remplacer le comportement par défaut.  
  
> [!NOTE]
> Lorsque `_MYTYPE` a la valeur « Custom », le projet contient l' `My` espace de noms, mais il ne contient aucun objet. Toutefois, l’affectation de la valeur `_MYTYPE` « Empty » empêche le compilateur d’ajouter l' `My` espace de noms et ses objets.  
  
 Ce tableau décrit les effets des valeurs prédéfinies des `_MY` constantes de compilation.  
  
|Constant|Signification|  
|--------------|-------------|  
|`_MYAPPLICATIONTYPE`|Active `My.Application` , si la constante est « console », « Windows » ou « WindowsForms » :<br /><br /> -La version « console » dérive de <xref:Microsoft.VisualBasic.ApplicationServices.ConsoleApplicationBase> . et contient moins de membres que la version « Windows ».<br />-La version « Windows » dérive de <xref:Microsoft.VisualBasic.ApplicationServices.ApplicationBase> et a moins de membres que la version « windowsforms ».<br />-La version « WindowsForms » de `My.Application` dérive de <xref:Microsoft.VisualBasic.ApplicationServices.WindowsFormsApplicationBase> . Si la `TARGET` constante est définie pour être « winexe », la classe comprend une `Sub Main` méthode.|  
|`_MYCOMPUTERTYPE`|Active `My.Computer` , si la constante est « Web » ou « Windows » :<br /><br /> -La version « Web » dérive de <xref:Microsoft.VisualBasic.Devices.ServerComputer> et a moins de membres que la version « Windows ».<br />-La version « Windows » de `My.Computer` dérive de <xref:Microsoft.VisualBasic.Devices.Computer> .|  
|`_MYFORMS`|Active `My.Forms` , si la constante est `TRUE` .|  
|`_MYUSERTYPE`|Active `My.User` , si la constante est « Web » ou « Windows » :<br /><br /> -La version « Web » de `My.User` est associée à l’identité de l’utilisateur de la requête HTTP actuelle.<br />-La version « Windows » de `My.User` est associée au principal actuel du thread.|  
|`_MYWEBSERVICES`|Active `My.WebServices` , si la constante est `TRUE` .|  
|`_MYTYPE`|Active `My.Log` , `My.Request` et `My.Response` , si la constante est « Web ».|  
  
## <a name="see-also"></a>Voir aussi

- <xref:Microsoft.VisualBasic.ApplicationServices.ApplicationBase>
- <xref:Microsoft.VisualBasic.Devices.Computer>
- <xref:Microsoft.VisualBasic.Logging.Log>
- <xref:Microsoft.VisualBasic.ApplicationServices.User>
- [Comment My dépend du type de projet](../development-with-my/how-my-depends-on-project-type.md)
- [Compilation conditionnelle](../../programming-guide/program-structure/conditional-compilation.md)
- [-définir (Visual Basic)](../../reference/command-line-compiler/define.md)
- [My.Forms, objet](../../language-reference/objects/my-forms-object.md)
- [My.Request, objet](../../language-reference/objects/my-request-object.md)
- [My.Response, objet](../../language-reference/objects/my-response-object.md)
- [My.WebServices, objet](../../language-reference/objects/my-webservices-object.md)
