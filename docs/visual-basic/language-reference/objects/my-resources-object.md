---
title: My.Resources, objet
ms.date: 07/20/2015
f1_keywords:
- My.Resources
- My.Resources.MyResources.ResourceManager
- My.Resources.MyResources.Culture
helpviewer_keywords:
- My.Resources object
ms.assetid: 34c3f2dc-7b87-432c-9d5f-17ea666bb266
ms.openlocfilehash: 2b7c82c31d2e31ccbf573cf1dfa138af2d99ce29
ms.sourcegitcommit: f8c270376ed905f6a8896ce0fe25b4f4b38ff498
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 06/04/2020
ms.locfileid: "84372455"
---
# <a name="myresources-object"></a>My.Resources, objet
Fournit des propriétés et des classes pour accéder aux ressources de l’application.  
  
## <a name="remarks"></a>Notes  
 L' `My.Resources` objet fournit l’accès aux ressources de l’application et vous permet de récupérer dynamiquement des ressources pour votre application. Pour plus d’informations, consultez [gestion des ressources d’une application (.net)](/visualstudio/ide/managing-application-resources-dotnet).  
  
 L' `My.Resources` objet expose uniquement les ressources globales. Il ne fournit pas d’accès aux fichiers de ressources associés aux formulaires. Vous devez accéder aux ressources du formulaire à partir du formulaire.  
  
 Vous pouvez accéder aux fichiers de ressources propres à la culture de l’application à partir de l' `My.Resources` objet. Par défaut, l' `My.Resources` objet recherche des ressources à partir du fichier de ressources qui correspond à la culture dans la <xref:Microsoft.VisualBasic.ApplicationServices.ApplicationBase.UICulture%2A> propriété. Toutefois, vous pouvez remplacer ce comportement et spécifier une culture particulière à utiliser pour les ressources. Pour plus d’informations, consultez [Ressources dans les applications de bureau](../../../framework/resources/index.md).  
  
## <a name="properties"></a>Propriétés  
 Les propriétés de l' `My.Resources` objet fournissent un accès en lecture seule aux ressources de votre application. Pour ajouter ou supprimer des ressources, utilisez le **Concepteur de projets**. Vous pouvez accéder aux ressources ajoutées par le biais du **Concepteur de projet** à l’aide de `My.Resources.` *resourceName*.  
  
 Vous pouvez également ajouter ou supprimer des fichiers de ressources en sélectionnant votre projet dans **Explorateur de solutions** et en cliquant sur **Ajouter un nouvel élément** ou **Ajouter un élément existant** dans le menu **projet** . Vous pouvez accéder aux ressources ajoutées de cette manière à l’aide de `My.Resources.` *resourceFileName* `.` *resourceName*.  
  
 Chaque ressource a un nom, une catégorie et une valeur, et ces paramètres de ressource déterminent la façon dont la propriété permettant d’accéder à la ressource s’affiche dans l' `My.Resources` objet. Pour les ressources ajoutées dans le **Concepteur de projet**:  
  
- Le nom détermine le nom de la propriété,  
  
- Les données de ressource sont la valeur de la propriété,  
  
- La catégorie détermine le type de la propriété :  
  
|Category|Type de données de propriété|  
|---|---|  
|**Chaînes**|[Chaîne](../data-types/string-data-type.md)|  
|**Images**|<xref:System.Drawing.Bitmap>|  
|**Icônes**|<xref:System.Drawing.Icon>|  
|**Audio**|<xref:System.IO.UnmanagedMemoryStream><br /><br /> La <xref:System.IO.UnmanagedMemoryStream> classe dérive de la <xref:System.IO.Stream> classe. elle peut donc être utilisée avec des méthodes qui acceptent des flux, telles que la <xref:Microsoft.VisualBasic.Devices.Audio.Play%2A> méthode.|  
|**Fichiers**|-   [Chaîne](../data-types/string-data-type.md) pour les fichiers texte.<br />-   <xref:System.Drawing.Bitmap>pour les fichiers image.<br />-   <xref:System.Drawing.Icon>pour les fichiers d’icône.<br />-   <xref:System.IO.UnmanagedMemoryStream>pour les fichiers audio.|  
|**Autres**|Déterminé par les informations de la colonne de **type** du concepteur.|  
  
## <a name="classes"></a>Classes  
 L' `My.Resources` objet expose chaque fichier de ressources en tant que classe avec des propriétés partagées. Le nom de la classe est le même que le nom du fichier de ressources. Comme décrit dans la section précédente, les ressources d’un fichier de ressources sont exposées en tant que propriétés dans la classe.  
  
## <a name="example"></a>Exemple  
 Cet exemple définit le titre d’un formulaire sur la ressource de type chaîne nommée `Form1Title` dans le fichier de ressources de l’application. Pour que l’exemple fonctionne, l’application doit avoir une chaîne nommée `Form1Title` dans son fichier de ressources.  
  
 [!code-vb[VbVbalrMyResources#1](~/samples/snippets/visualbasic/VS_Snippets_VBCSharp/VbVbalrMyResources/VB/Form1.vb#1)]  
  
## <a name="example"></a>Exemple  
 Cet exemple définit l’icône du formulaire sur l’icône nommée `Form1Icon` qui est stockée dans le fichier de ressources de l’application. Pour que l’exemple fonctionne, l’application doit avoir une icône nommée `Form1Icon` dans son fichier de ressources.  
  
 [!code-vb[VbVbalrMyResources#2](~/samples/snippets/visualbasic/VS_Snippets_VBCSharp/VbVbalrMyResources/VB/Form1.vb#2)]  
  
## <a name="example"></a>Exemple  
 Cet exemple définit l’image d’arrière-plan d’un formulaire sur la ressource d’image nommée `Form1Background` , qui se trouve dans le fichier de ressources de l’application. Pour que cet exemple fonctionne, l’application doit avoir une ressource image nommée `Form1Background` dans son fichier de ressources.  
  
 [!code-vb[VbVbalrMyResources#3](~/samples/snippets/visualbasic/VS_Snippets_VBCSharp/VbVbalrMyResources/VB/Form1.vb#3)]  
  
## <a name="example"></a>Exemple  
 Cet exemple lit le son qui est stocké en tant que ressource audio nommée `Form1Greeting` dans le fichier de ressources de l’application. Pour que l’exemple fonctionne, l’application doit avoir une ressource audio nommée `Form1Greeting` dans son fichier de ressources. La `My.Computer.Audio.Play` méthode est disponible uniquement pour les applications Windows Forms.  
  
 [!code-vb[VbVbalrMyResources#4](~/samples/snippets/visualbasic/VS_Snippets_VBCSharp/VbVbalrMyResources/VB/Form1.vb#4)]  
  
## <a name="example"></a>Exemple  
 Cet exemple récupère la version de la culture française d’une ressource de type chaîne de l’application. La ressource est nommée `Message` . Pour modifier la culture utilisée par l' `My.Resources` objet, l’exemple utilise <xref:Microsoft.VisualBasic.ApplicationServices.ApplicationBase.ChangeUICulture%2A> .  
  
 Pour que cet exemple fonctionne, l’application doit avoir une chaîne nommée `Message` dans son fichier de ressources, et l’application doit avoir la version de culture française de ce fichier de ressources, Resources.fr-fr. resx. Si l’application n’a pas la version de culture française du fichier de ressources, l' `My.Resource` objet récupère la ressource à partir du fichier de ressources de culture par défaut.  
  
 [!code-vb[VbVbalrMyResources#10](~/samples/snippets/visualbasic/VS_Snippets_VBCSharp/VbVbalrMyResources/VB/Form1.vb#10)]  
  
## <a name="see-also"></a>Voir aussi

- [Gestion des ressources d'une application (.NET)](/visualstudio/ide/managing-application-resources-dotnet)
- [Ressources dans les applications de bureau](../../../framework/resources/index.md)
