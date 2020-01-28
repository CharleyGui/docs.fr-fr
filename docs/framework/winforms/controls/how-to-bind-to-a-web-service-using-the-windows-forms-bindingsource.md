---
title: Liaison à un service Web à l’aide de BindingSource
ms.date: 03/30/2017
dev_langs:
- csharp
- vb
- cpp
helpviewer_keywords:
- Web services [Windows Forms], binding controls
- BindingSource component [Windows Forms], binding to a Web service
- examples [Windows Forms], BindingSource component
- controls [Windows Forms], binding to Web service
- BindingSource component [Windows Forms], examples
ms.assetid: ee261207-4573-4cb9-a8cb-5185037e0fba
ms.openlocfilehash: 0680c73e578577cf40158761f6c635fe30ff9f4d
ms.sourcegitcommit: de17a7a0a37042f0d4406f5ae5393531caeb25ba
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 01/24/2020
ms.locfileid: "76746683"
---
# <a name="how-to-bind-to-a-web-service-using-the-windows-forms-bindingsource"></a>Comment : établir une liaison à un service Web à l’aide du BindingSource Windows Forms
Si vous voulez lier un contrôle Windows Forms aux résultats obtenus à partir d'un appel à un service web XML, vous pouvez utiliser un composant <xref:System.Windows.Forms.BindingSource>. Cette procédure est similaire à celle d'une liaison d'un composant <xref:System.Windows.Forms.BindingSource> à un type. Vous devez créer un proxy côté client qui contienne les méthodes et les types exposés par le service web. Vous générez un proxy côté client à partir du service web (.asmx) lui-même ou à partir de son fichier WSDL. En outre, votre proxy côté client doit exposer les champs de types complexes utilisés par le service web en tant que propriétés publiques. Vous pouvez ensuite lier la <xref:System.Windows.Forms.BindingSource> à l'un des types exposés dans le proxy du service web.  
  
### <a name="to-create-and-bind-to-a-client-side-proxy"></a>Pour créer un proxy côté client et créer des liaisons à celui-ci  
  
1. Créez un formulaire Windows dans le répertoire de votre choix, avec un espace de noms approprié.  
  
2. Ajoutez un composant <xref:System.Windows.Forms.BindingSource> au formulaire.  
  
3. Ouvrez l’invite de commandes du kit de développement logiciel (SDK) Windows et accédez au même répertoire que celui dans lequel se trouve votre formulaire.  
  
4. À l’aide de l’outil WSDL, entrez `wsdl` et l’URL du fichier .asmx ou WSDL du service web, suivi de l’espace de noms de votre application, et éventuellement le langage utilisé.  
  
     L’exemple de code suivant utilise le service Web situé dans `http://webservices.eraserver.net/zipcoderesolver/zipcoderesolver.asmx`. Par exemple, pour un type C# `wsdl http://webservices.eraserver.net.zipcoderesolver/zipcoderesolver.asmx /n:BindToWebService` ou pour un type Visual Basic `wsdl http://webservices.eraserver.net.zipcoderesolver/zipcoderesolver.asmx /n:BindToWebService /language:VB`. Le fait de passer le chemin d’accès en tant qu’argument à l’outil WSDL génère un proxy côté client dans le même répertoire et le même espace de noms que votre application, dans le langage spécifié. Si vous utilisez Visual Studio, ajoutez le fichier à votre projet.  
  
5. Sélectionnez un type dans le proxy côté client avec lequel créer une liaison.  
  
     Il s'agit généralement d'un type retourné par une méthode fournie par le service web. Les champs du type choisi doivent être exposés en tant que propriétés publiques pour la liaison.  
  
     [!code-cpp[System.Windows.Forms.DataConnectorWebService#4](~/samples/snippets/cpp/VS_Snippets_Winforms/System.Windows.Forms.DataConnectorWebService/CPP/form1.cpp#4)]
     [!code-csharp[System.Windows.Forms.DataConnectorWebService#4](~/samples/snippets/csharp/VS_Snippets_Winforms/System.Windows.Forms.DataConnectorWebService/CS/form1.cs#4)]
     [!code-vb[System.Windows.Forms.DataConnectorWebService#4](~/samples/snippets/visualbasic/VS_Snippets_Winforms/System.Windows.Forms.DataConnectorWebService/VB/form1.vb#4)]  
  
6. Définissez la propriété <xref:System.Windows.Forms.BindingSource.DataSource%2A> de <xref:System.Windows.Forms.BindingSource> sur le type contenu dans le proxy côté client du service web.  
  
     [!code-cpp[System.Windows.Forms.DataConnectorWebService#2](~/samples/snippets/cpp/VS_Snippets_Winforms/System.Windows.Forms.DataConnectorWebService/CPP/form1.cpp#2)]
     [!code-csharp[System.Windows.Forms.DataConnectorWebService#2](~/samples/snippets/csharp/VS_Snippets_Winforms/System.Windows.Forms.DataConnectorWebService/CS/form1.cs#2)]
     [!code-vb[System.Windows.Forms.DataConnectorWebService#2](~/samples/snippets/visualbasic/VS_Snippets_Winforms/System.Windows.Forms.DataConnectorWebService/VB/form1.vb#2)]  
  
### <a name="to-bind-controls-to-the-bindingsource-that-is-bound-to-a-web-service"></a>Pour lier des contrôles à une BindingSource liée à un service web  
  
- Liez des contrôles à <xref:System.Windows.Forms.BindingSource>, en passant la propriété publique du type de service web de votre choix en tant que paramètre.  
  
     [!code-cpp[System.Windows.Forms.DataConnectorWebService#3](~/samples/snippets/cpp/VS_Snippets_Winforms/System.Windows.Forms.DataConnectorWebService/CPP/form1.cpp#3)]
     [!code-csharp[System.Windows.Forms.DataConnectorWebService#3](~/samples/snippets/csharp/VS_Snippets_Winforms/System.Windows.Forms.DataConnectorWebService/CS/form1.cs#3)]
     [!code-vb[System.Windows.Forms.DataConnectorWebService#3](~/samples/snippets/visualbasic/VS_Snippets_Winforms/System.Windows.Forms.DataConnectorWebService/VB/form1.vb#3)]  
  
## <a name="example"></a>Exemple  
 L'exemple de code suivant montre comment lier un composant <xref:System.Windows.Forms.BindingSource> à un service web, puis comment lier une zone de texte au composant <xref:System.Windows.Forms.BindingSource>. Quand vous cliquez sur le bouton, une méthode de service web est appelée et les résultats s'affichent dans `textbox1`.  
  
 [!code-cpp[System.Windows.Forms.DataConnectorWebService#1](~/samples/snippets/cpp/VS_Snippets_Winforms/System.Windows.Forms.DataConnectorWebService/CPP/form1.cpp#1)]
 [!code-csharp[System.Windows.Forms.DataConnectorWebService#1](~/samples/snippets/csharp/VS_Snippets_Winforms/System.Windows.Forms.DataConnectorWebService/CS/form1.cs#1)]
 [!code-vb[System.Windows.Forms.DataConnectorWebService#1](~/samples/snippets/visualbasic/VS_Snippets_Winforms/System.Windows.Forms.DataConnectorWebService/VB/form1.vb#1)]  
  
## <a name="compiling-the-code"></a>Compilation du code  
 Il s'agit d'un exemple complet qui inclut une méthode `Main` et une version raccourcie du code du proxy côté client.  
  
 Cet exemple nécessite :  
  
- Des références aux assemblys System, System.Drawing, System.Web.Services, System.Windows.Forms et System.Xml.  
  
## <a name="see-also"></a>Voir aussi

- [BindingSource, composant](bindingsource-component.md)
- [Comment : lier un contrôle Windows Forms à un type](how-to-bind-a-windows-forms-control-to-a-type.md)
