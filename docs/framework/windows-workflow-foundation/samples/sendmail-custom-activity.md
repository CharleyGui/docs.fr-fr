---
title: Activité personnalisée SendMail
ms.date: 03/30/2017
ms.assetid: 947a9ae6-379c-43a3-9cd5-87f573a5739f
ms.openlocfilehash: f518beebe336080853e4dec3bca6f8539bbec304
ms.sourcegitcommit: bc293b14af795e0e999e3304dd40c0222cf2ffe4
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 11/26/2020
ms.locfileid: "96267587"
---
# <a name="sendmail-custom-activity"></a>Activité personnalisée SendMail

Cet exemple montre comment créer une activité personnalisée dérivée de <xref:System.Activities.AsyncCodeActivity> pour envoyer du courrier à l'aide de SMTP afin de l'utiliser dans une application de workflow. L’activité personnalisée utilise les fonctionnalités de <xref:System.Net.Mail.SmtpClient> pour envoyer des courriers électroniques de manière asynchrone et pour envoyer du courrier électronique avec l’authentification. Elle fournit aussi certaines fonctionnalités d'utilisateur final telles que le mode Test, le remplacement des jetons, les modèles de fichier et le chemin d'accès de dépôt de test.  
  
 Le tableau suivant décrit en détail les arguments pour l’activité `SendMail`.  
  
|Nom|Type|Description|  
|-|-|-|  
|Host|String|Adresse du serveur hôte SMTP.|  
|Port|String|Port du service SMTP dans l'hôte.|  
|EnableSsl|bool|Indique si <xref:System.Net.Mail.SmtpClient> utilise le protocole SSL (Secure Sockets Layer) pour chiffrer la connexion.|  
|UserName|String|Nom d'utilisateur pour définir les informations d'identification utilisées pour authentifier la propriété <xref:System.Net.Mail.SmtpClient.Credentials%2A> de l'expéditeur.|  
|Mot de passe|String|Mot de passe pour définir les informations d'identification utilisées pour authentifier la propriété <xref:System.Net.Mail.SmtpClient.Credentials%2A> de l'expéditeur.|  
|Objet|<xref:System.Activities.InArgument%601>\<string>|Sujet du message.|  
|Corps|<xref:System.Activities.InArgument%601>\<string>|Corps du message.|  
|Pièces jointes|<xref:System.Activities.InArgument%601>\<string>|Collection de pièces jointes utilisée pour stocker les données jointes à ce message électronique.|  
|Du|<xref:System.Net.Mail.MailAddress>|Adresse de l’adresse de ce message électronique.|  
|À|<xref:System.Activities.InArgument%601>\<<xref:System.Net.Mail.MailAddressCollection>>|Collection d’adresses qui contient les destinataires de ce message électronique.|  
|CC|<xref:System.Activities.InArgument%601>\<<xref:System.Net.Mail.MailAddressCollection>>|Collection d’adresses qui contient les destinataires de copie carbone (CC) pour ce message électronique.|  
|BCC|<xref:System.Activities.InArgument%601>\<<xref:System.Net.Mail.MailAddressCollection>>|Collection d’adresses qui contient les destinataires de copie carbone invisible (CCI) pour ce message électronique.|  
|Jetons|<xref:System.Activities.InArgument%601><IDictionary\<string, string>>|Jetons à remplacer dans le corps. Cette fonctionnalité permet aux utilisateurs de spécifier certaines valeurs dans le corps qui peuvent être remplacées ultérieurement par les jetons fournis à l’aide de cette propriété.|  
|BodyTemplateFilePath|String|Chemin d'accès à un modèle de corps. L'activité `SendMail` copie le contenu de ce fichier dans sa propriété de corps.<br /><br /> Ce modèle peut contenir des jetons qui sont remplacés par le contenu de la propriété des jetons.|  
|TestMailTo|<xref:System.Net.Mail.MailAddress>|Lorsque cette propriété est définie, tous les messages électroniques sont envoyés à l’adresse spécifiée dans celle-ci.<br /><br /> Cette propriété n'est pas conçue pour une utilisation lors du test des workflows. Par exemple, lorsque vous souhaitez vous assurer que tous les courriers électroniques sont envoyés sans les envoyer aux destinataires réels.|  
|TestDropPath|String|Lorsque cette propriété est définie, tous les courriers électroniques sont également enregistrés dans le fichier spécifié.<br /><br /> Cette propriété est destinée à être utilisée lorsque vous testez ou déboguez des flux de travail pour vous assurer que le format et le contenu des messages sortants sont appropriés.|  
  
## <a name="solution-contents"></a>Contenu de la solution  

 La solution contient deux projets.  
  
|Projet|Description|Fichiers importants|  
|-------------|-----------------|---------------------|  
|SendMail|Activité SendMail|1. SendMail.cs : implémentation de l’activité principale<br />2. SendMailDesigner. xaml et SendMailDesigner.xaml.cs : Designer pour l’activité SendMail<br />3. MailTemplateBody.htm : modèle de l’e-mail à envoyer.|  
|SendMailTestClient|Client pour tester l'activité SendMail.  Ce projet illustre deux façons d'appeler l'activité SendMail : déclarative et par programme.|1. Sequence1. xaml : workflow qui appelle l’activité SendMail.<br />2. Program.cs : appelle Sequence1 et crée également un workflow par programme qui utilise SendMail.|  
  
## <a name="further-configuration-of-the-sendmail-activity"></a>Configuration supplémentaire de l'activité SendMail  

 Bien qu'elle ne soit pas illustrée dans l'exemple, les utilisateurs peuvent effectuer une configuration supplémentaire de l'activité SendMail. Les trois sections suivantes montrent comment procéder.  
  
### <a name="sending-an-email-using-tokens-specified-in-the-body"></a>Envoi d'un message électronique à l'aide de jetons spécifiés dans le corps  

 Cet extrait de code montre comment envoyer un message électronique avec des jetons dans le corps. Notez la façon dont les jetons sont fournis dans la propriété de corps. Les valeurs pour ces jetons sont fournies à la propriété de jetons.  
  
```csharp  
IDictionary<string, string> tokens = new Dictionary<string, string>();  
tokens.Add("@name", "John Doe");  
tokens.Add("@date", DateTime.Now.ToString());  
tokens.Add("@server", "localhost");  
  
new SendMail  
{  
    From = new LambdaValue<MailAddress>(ctx => new MailAddress("john.doe@contoso.com")),  
    To = new LambdaValue<MailAddressCollection>(  
                    ctx => new MailAddressCollection() { new MailAddress("someone@microsoft.com") }),  
    Subject = "Test email",  
    Body = "Hello @name. This is a test email sent from @server. Current date is @date",  
    Host = "localhost",  
    Port = 25,  
    Tokens = new LambdaValue<IDictionary<string, string>>(ctx => tokens)  
};  
```  
  
### <a name="sending-an-email-using-a-template"></a>Envoi d'un message électronique à l'aide d'un modèle  

 Cet extrait de code montre comment envoyer un message électronique à l'aide de jetons de modèle dans le corps. Notez que lorsque vous définissez la propriété `BodyTemplateFilePath`, il n'est pas nécessaire de fournir la valeur pour la propriété Body (le contenu du modèle sera copié dans le corps).  
  
```csharp  
new SendMail  
{
    From = new LambdaValue<MailAddress>(ctx => new MailAddress("john.doe@contoso.com")),  
    To = new LambdaValue<MailAddressCollection>(  
                    ctx => new MailAddressCollection() { new MailAddress("someone@microsoft.com") }),  
    Subject = "Test email",  
    Host = "localhost",  
    Port = 25,  
    Tokens = new LambdaValue<IDictionary<string, string>>(ctx => tokens),  
    BodyTemplateFilePath = @"..\..\..\SendMail\Templates\MailTemplateBody.htm",
};  
```  
  
### <a name="sending-mails-in-testing-mode"></a>Envoi de messages électronique en mode Test  

 Cet extrait de code montre comment définir les deux propriétés de test : en définissant `TestMailTo` sur tous les messages seront envoyés à `john.doe@contoso.con` (sans tenir compte des valeurs de à, CC, CCI). En définissant TestDropPath, tous les messages électroniques sortants seront aussi enregistrés dans le chemin d'accès fourni. Ces propriétés peuvent être définies indépendamment (elles ne sont pas liées).  
  
```csharp  
new SendMail  
{
   From = new LambdaValue<MailAddress>(ctx => new MailAddress("john.doe@contoso.com")),  
   To = new LambdaValue<MailAddressCollection>(  
                    ctx => new MailAddressCollection() { new MailAddress("someone@microsoft.com") }),  
   Subject = "Test email",  
   Host = "localhost",  
   Port = 25,  
   Tokens = new LambdaValue<IDictionary<string, string>>(ctx => tokens),  
   BodyTemplateFilePath = @"..\..\..\SendMail\Templates\MailTemplateBody.htm",  
   TestMailTo= new LambdaValue<MailAddress>(ctx => new MailAddress("john.doe@contoso.com")),  
   TestDropPath = @"c:\Samples\SendMail\TestDropPath\",  
};  
```  
  
## <a name="set-up-instructions"></a>Instructions d'installation  

 Vous devez avoir accès à un serveur SMTP pour cet exemple.  
  
 Pour plus d’informations sur la configuration d’un serveur SMTP, consultez les liens suivants.  
  
- [Configuration du service SMTP (IIS 6.0)](/previous-versions/windows/it-pro/windows-server-2003/cc784968(v=ws.10))  
  
- [IIS 7.0 : Configuration d'un courrier électronique SMTP](/previous-versions/windows/it-pro/windows-server-2008-R2-and-2008/cc772058(v=ws.10))  
  
- [Procédure : installer le service SMTP](/previous-versions/tn-archive/aa997480(v=exchg.65))  
  
 Les émulateurs SMTP fournis par des tiers ne sont pas disponibles pour le téléchargement.  
  
##### <a name="to-run-this-sample"></a>Pour exécuter l'exemple  
  
1. À l’aide de Visual Studio 2010, ouvrez le fichier solution SendMail. sln.  
  
2. Vérifiez que vous avez accès à un serveur SMTP valide. Consultez les instructions d'installation.  
  
3. Configurez le programme avec l’adresse de votre serveur et les adresses de messagerie de et à.  
  
     Pour exécuter correctement cet exemple, vous devrez peut-être configurer la valeur de et vers les adresses de messagerie et l’adresse du serveur SMTP dans Program.cs et dans Sequence. Xaml. Vous devrez modifier l'adresse à ces deux emplacements car le programme envoie les messages de différentes façons.  
  
4. Pour générer la solution, appuyez sur Ctrl+Maj+B.  
  
5. Pour exécuter la solution, appuyez sur Ctrl+F5.  
  
> [!IMPORTANT]
> Les exemples peuvent déjà être installés sur votre ordinateur. Recherchez le répertoire (par défaut) suivant avant de continuer.  
>
> `<InstallDrive>:\WF_WCF_Samples`  
>
> Si ce répertoire n’existe pas, accédez à [Windows Communication Foundation (WCF) et Windows Workflow Foundation (WF) exemples pour .NET Framework 4](https://www.microsoft.com/download/details.aspx?id=21459) pour télécharger tous les exemples Windows Communication Foundation (WCF) et [!INCLUDE[wf1](../../../../includes/wf1-md.md)] . Cet exemple se trouve dans le répertoire suivant.  
>
> `<InstallDrive>:\WF_WCF_Samples\WF\Scenario\ActivityLibrary\SendMail`
