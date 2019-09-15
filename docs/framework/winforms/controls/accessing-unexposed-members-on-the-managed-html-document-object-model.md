---
title: Accès aux membres non exposés sur le modèle objet de document HTML managé
ms.date: 03/30/2017
dev_langs:
- csharp
- vb
helpviewer_keywords:
- unexposed members
- managed HTML DOM [Windows Forms], accessing unexposed members
ms.assetid: 762295bd-2355-4aa7-b43c-5bff997a33e6
ms.openlocfilehash: 525ef52ecbbc61fba787fa8286c56c638d837faf
ms.sourcegitcommit: 005980b14629dfc193ff6cdc040800bc75e0a5a5
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 09/14/2019
ms.locfileid: "70988405"
---
# <a name="accessing-unexposed-members-on-the-managed-html-document-object-model"></a>Accès aux membres non exposés sur le modèle objet de document HTML managé
Le document Object Model HTML managé contient une classe appelée <xref:System.Windows.Forms.HtmlElement> qui expose les propriétés, les méthodes et les événements que tous les éléments HTML ont en commun. Toutefois, il est parfois nécessaire d’accéder aux membres que l’interface managée n’expose pas directement. Cette rubrique examine deux façons d’accéder à des membres non exposés, y compris des fonctions JScript et VBScript définies dans une page Web.  
  
## <a name="accessing-unexposed-members-through-managed-interfaces"></a>Accès aux membres non exposés via des interfaces managées  
 <xref:System.Windows.Forms.HtmlDocument>et <xref:System.Windows.Forms.HtmlElement> fournissent quatre méthodes qui permettent d’accéder à des membres non exposés. Le tableau suivant répertorie les types et leurs méthodes correspondantes.  
  
|Type de membre|Méthode (s)|  
|-----------------|-----------------|  
|Propriétés (<xref:System.Windows.Forms.HtmlElement>)|<xref:System.Windows.Forms.HtmlElement.GetAttribute%2A><br /><br /> <xref:System.Windows.Forms.HtmlElement.SetAttribute%2A>|  
|Méthodes|<xref:System.Windows.Forms.HtmlElement.InvokeMember%2A>|  
|Événements (<xref:System.Windows.Forms.HtmlDocument>)|<xref:System.Windows.Forms.HtmlDocument.AttachEventHandler%2A><br /><br /> <xref:System.Windows.Forms.HtmlDocument.DetachEventHandler%2A>|  
|Événements (<xref:System.Windows.Forms.HtmlElement>)|<xref:System.Windows.Forms.HtmlElement.AttachEventHandler%2A><br /><br /> <xref:System.Windows.Forms.HtmlElement.DetachEventHandler%2A>|  
|Événements (<xref:System.Windows.Forms.HtmlWindow>)|<xref:System.Windows.Forms.HtmlWindow.AttachEventHandler%2A><br /><br /> <xref:System.Windows.Forms.HtmlWindow.DetachEventHandler%2A>|  
  
 Lorsque vous utilisez ces méthodes, il est supposé que vous avez un élément du type sous-jacent correct. Supposons que vous souhaitez écouter l' `Submit` événement d’un `FORM` élément sur une page HTML, afin de pouvoir effectuer un pré-traitement sur les `FORM`valeurs de avant que l’utilisateur ne les envoie au serveur. Dans l’idéal, si vous contrôlez le code HTML, vous devez définir `FORM` le pour qu’il `ID` dispose d’un attribut unique.  
  
```html  
<HTML>  
  
    <HEAD>  
        <TITLE>Form Page</TITLE>  
    </HEAD>  
  
    <BODY>  
        <FORM ID="form1">  
             ... form fields defined here ...  
        </FORM>  
    </BODY>  
  
</HTML>  
```  
  
 Après avoir chargé cette page dans le <xref:System.Windows.Forms.WebBrowser> contrôle, vous pouvez utiliser la <xref:System.Windows.Forms.HtmlDocument.GetElementById%2A> méthode pour récupérer `FORM` au moment de l’exécution `form1` à l’aide de comme argument.  
  
 [!code-csharp[System.Windows.Forms.HtmlElement#10](~/samples/snippets/csharp/VS_Snippets_Winforms/System.Windows.Forms.HtmlElement/CS/Form1.cs#10)]
 [!code-vb[System.Windows.Forms.HtmlElement#10](~/samples/snippets/visualbasic/VS_Snippets_Winforms/System.Windows.Forms.HtmlElement/VB/Form1.vb#10)]  
  
## <a name="accessing-unmanaged-interfaces"></a>Accès aux interfaces non managées  
 Vous pouvez également accéder aux membres non exposés sur le modèle DOM HTML managé à l’aide des interfaces COM (Component Object Model) non managées exposées par chaque classe DOM. Cela est recommandé si vous devez effectuer plusieurs appels sur des membres non exposés, ou si les membres non exposés retournent d’autres interfaces non managées qui ne sont pas encapsulées par le DOM HTML managé.  
  
 Le tableau suivant répertorie toutes les interfaces non managées exposées via le modèle DOM HTML managé. Cliquez sur chaque lien pour obtenir une explication de son utilisation et un exemple de code.  
  
|Type|Interface non managée|  
|----------|-------------------------|  
|<xref:System.Windows.Forms.HtmlDocument>|<xref:System.Windows.Forms.HtmlDocument.DomDocument%2A>|  
|<xref:System.Windows.Forms.HtmlElement>|<xref:System.Windows.Forms.HtmlElement.DomElement%2A>|  
|<xref:System.Windows.Forms.HtmlWindow>|<xref:System.Windows.Forms.HtmlWindow.DomWindow%2A>|  
|<xref:System.Windows.Forms.HtmlHistory>|<xref:System.Windows.Forms.HtmlHistory.DomHistory%2A>|  
  
 Le moyen le plus simple d’utiliser les interfaces COM consiste à ajouter une référence à la bibliothèque DOM HTML non managée (MSHTML. dll) à partir de votre application, bien que cela ne soit pas pris en charge. Pour plus d’informations, consultez [l’Article 934368](https://support.microsoft.com/kb/934368)de la base de connaissances.  
  
## <a name="accessing-script-functions"></a>Accès aux fonctions de script  
 Une page HTML peut définir une ou plusieurs fonctions à l’aide d’un langage de script tel que JScript ou VBScript. Ces fonctions sont placées à l' `SCRIPT` intérieur d’une page de la page et peuvent être exécutées à la demande ou en réponse à un événement sur le DOM.  
  
 Vous pouvez appeler n’importe quelle fonction de script que vous définissez dans une <xref:System.Windows.Forms.HtmlDocument.InvokeScript%2A> page HTML à l’aide de la méthode. Si la méthode de script retourne un élément HTML, vous pouvez utiliser un cast pour convertir ce résultat de retour <xref:System.Windows.Forms.HtmlElement>en. Pour plus d’informations et pour obtenir <xref:System.Windows.Forms.HtmlDocument.InvokeScript%2A>un exemple de code, consultez.  
  
## <a name="see-also"></a>Voir aussi

- [Utilisation du modèle DOM HTML managé](using-the-managed-html-document-object-model.md)
