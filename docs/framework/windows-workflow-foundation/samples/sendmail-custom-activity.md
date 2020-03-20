---
title: Activité personnalisée SendMail
ms.date: 03/30/2017
ms.assetid: 947a9ae6-379c-43a3-9cd5-87f573a5739f
ms.openlocfilehash: e7cc64e68c3d78b9ee7ec813700e96a52c239141
ms.sourcegitcommit: 7588136e355e10cbc2582f389c90c127363c02a5
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 03/12/2020
ms.locfileid: "79182781"
---
# <a name="sendmail-custom-activity"></a><span data-ttu-id="6b5fb-102">Activité personnalisée SendMail</span><span class="sxs-lookup"><span data-stu-id="6b5fb-102">SendMail Custom Activity</span></span>
<span data-ttu-id="6b5fb-103">Cet exemple montre comment créer une activité personnalisée dérivée de <xref:System.Activities.AsyncCodeActivity> pour envoyer du courrier à l'aide de SMTP afin de l'utiliser dans une application de workflow.</span><span class="sxs-lookup"><span data-stu-id="6b5fb-103">This sample demonstrates how to create a custom activity that derives from <xref:System.Activities.AsyncCodeActivity> to send mail using SMTP for use within a workflow application.</span></span> <span data-ttu-id="6b5fb-104">L’activité personnalisée utilise <xref:System.Net.Mail.SmtpClient> les capacités d’envoyer des e-mails asynchronement et d’envoyer du courrier avec authentification.</span><span class="sxs-lookup"><span data-stu-id="6b5fb-104">The custom activity uses the capabilities of <xref:System.Net.Mail.SmtpClient> to send email asynchronously and to send mail with authentication.</span></span> <span data-ttu-id="6b5fb-105">Elle fournit aussi certaines fonctionnalités d'utilisateur final telles que le mode Test, le remplacement des jetons, les modèles de fichier et le chemin d'accès de dépôt de test.</span><span class="sxs-lookup"><span data-stu-id="6b5fb-105">It also provides some end-user features like test mode, token replacement, file templates, and test drop path.</span></span>  
  
 <span data-ttu-id="6b5fb-106">Le tableau suivant décrit en détail les arguments pour l’activité `SendMail`.</span><span class="sxs-lookup"><span data-stu-id="6b5fb-106">The following table details the arguments for the `SendMail` activity.</span></span>  
  
|<span data-ttu-id="6b5fb-107">Nom</span><span class="sxs-lookup"><span data-stu-id="6b5fb-107">Name</span></span>|<span data-ttu-id="6b5fb-108">Type</span><span class="sxs-lookup"><span data-stu-id="6b5fb-108">Type</span></span>|<span data-ttu-id="6b5fb-109">Description</span><span class="sxs-lookup"><span data-stu-id="6b5fb-109">Description</span></span>|  
|-|-|-|  
|<span data-ttu-id="6b5fb-110">Host</span><span class="sxs-lookup"><span data-stu-id="6b5fb-110">Host</span></span>|<span data-ttu-id="6b5fb-111">String</span><span class="sxs-lookup"><span data-stu-id="6b5fb-111">String</span></span>|<span data-ttu-id="6b5fb-112">Adresse du serveur hôte SMTP.</span><span class="sxs-lookup"><span data-stu-id="6b5fb-112">Address of the SMTP server host.</span></span>|  
|<span data-ttu-id="6b5fb-113">Port</span><span class="sxs-lookup"><span data-stu-id="6b5fb-113">Port</span></span>|<span data-ttu-id="6b5fb-114">String</span><span class="sxs-lookup"><span data-stu-id="6b5fb-114">String</span></span>|<span data-ttu-id="6b5fb-115">Port du service SMTP dans l'hôte.</span><span class="sxs-lookup"><span data-stu-id="6b5fb-115">Port of the SMTP service in the host.</span></span>|  
|<span data-ttu-id="6b5fb-116">EnableSsl</span><span class="sxs-lookup"><span data-stu-id="6b5fb-116">EnableSsl</span></span>|<span data-ttu-id="6b5fb-117">bool</span><span class="sxs-lookup"><span data-stu-id="6b5fb-117">bool</span></span>|<span data-ttu-id="6b5fb-118">Indique si <xref:System.Net.Mail.SmtpClient> utilise le protocole SSL (Secure Sockets Layer) pour chiffrer la connexion.</span><span class="sxs-lookup"><span data-stu-id="6b5fb-118">Specifies whether the <xref:System.Net.Mail.SmtpClient> uses Secure Sockets Layer (SSL) to encrypt the connection.</span></span>|  
|<span data-ttu-id="6b5fb-119">UserName</span><span class="sxs-lookup"><span data-stu-id="6b5fb-119">UserName</span></span>|<span data-ttu-id="6b5fb-120">String</span><span class="sxs-lookup"><span data-stu-id="6b5fb-120">String</span></span>|<span data-ttu-id="6b5fb-121">Nom d'utilisateur pour définir les informations d'identification utilisées pour authentifier la propriété <xref:System.Net.Mail.SmtpClient.Credentials%2A> de l'expéditeur.</span><span class="sxs-lookup"><span data-stu-id="6b5fb-121">Username to set up the credentials to authenticate the sender <xref:System.Net.Mail.SmtpClient.Credentials%2A> property.</span></span>|  
|<span data-ttu-id="6b5fb-122">Mot de passe</span><span class="sxs-lookup"><span data-stu-id="6b5fb-122">Password</span></span>|<span data-ttu-id="6b5fb-123">String</span><span class="sxs-lookup"><span data-stu-id="6b5fb-123">String</span></span>|<span data-ttu-id="6b5fb-124">Mot de passe pour définir les informations d'identification utilisées pour authentifier la propriété <xref:System.Net.Mail.SmtpClient.Credentials%2A> de l'expéditeur.</span><span class="sxs-lookup"><span data-stu-id="6b5fb-124">Password to set up the credentials to authenticate the sender <xref:System.Net.Mail.SmtpClient.Credentials%2A> property.</span></span>|  
|<span data-ttu-id="6b5fb-125">Objet</span><span class="sxs-lookup"><span data-stu-id="6b5fb-125">Subject</span></span>|<span data-ttu-id="6b5fb-126"><xref:System.Activities.InArgument%601>\<> de cordes</span><span class="sxs-lookup"><span data-stu-id="6b5fb-126"><xref:System.Activities.InArgument%601>\<string></span></span>|<span data-ttu-id="6b5fb-127">Sujet du message.</span><span class="sxs-lookup"><span data-stu-id="6b5fb-127">Subject of the message.</span></span>|  
|<span data-ttu-id="6b5fb-128">body</span><span class="sxs-lookup"><span data-stu-id="6b5fb-128">Body</span></span>|<span data-ttu-id="6b5fb-129"><xref:System.Activities.InArgument%601>\<> de cordes</span><span class="sxs-lookup"><span data-stu-id="6b5fb-129"><xref:System.Activities.InArgument%601>\<string></span></span>|<span data-ttu-id="6b5fb-130">Corps du message.</span><span class="sxs-lookup"><span data-stu-id="6b5fb-130">Body of the message.</span></span>|  
|<span data-ttu-id="6b5fb-131">Pièces jointes</span><span class="sxs-lookup"><span data-stu-id="6b5fb-131">Attachments</span></span>|<span data-ttu-id="6b5fb-132"><xref:System.Activities.InArgument%601>\<> de cordes</span><span class="sxs-lookup"><span data-stu-id="6b5fb-132"><xref:System.Activities.InArgument%601>\<string></span></span>|<span data-ttu-id="6b5fb-133">Collection de pièces jointes utilisée pour stocker les données jointes à ce message électronique.</span><span class="sxs-lookup"><span data-stu-id="6b5fb-133">Attachment collection used to store data attached to this email message.</span></span>|  
|<span data-ttu-id="6b5fb-134">À partir</span><span class="sxs-lookup"><span data-stu-id="6b5fb-134">From</span></span>|<xref:System.Net.Mail.MailAddress>|<span data-ttu-id="6b5fb-135">De l’adresse pour ce message électronique.</span><span class="sxs-lookup"><span data-stu-id="6b5fb-135">From address for this email message.</span></span>|  
|<span data-ttu-id="6b5fb-136">À</span><span class="sxs-lookup"><span data-stu-id="6b5fb-136">To</span></span>|<xref:System.Activities.InArgument%601>\<<xref:System.Net.Mail.MailAddressCollection>>|<span data-ttu-id="6b5fb-137">Collection d’adresses qui contient les destinataires de ce message électronique.</span><span class="sxs-lookup"><span data-stu-id="6b5fb-137">Address collection that contains the recipients of this email message.</span></span>|  
|<span data-ttu-id="6b5fb-138">CC</span><span class="sxs-lookup"><span data-stu-id="6b5fb-138">CC</span></span>|<xref:System.Activities.InArgument%601>\<<xref:System.Net.Mail.MailAddressCollection>>|<span data-ttu-id="6b5fb-139">Collection d’adresses qui contient les destinataires de la copie carbone (CC) pour ce message électronique.</span><span class="sxs-lookup"><span data-stu-id="6b5fb-139">Address collection that contains the carbon copy (CC) recipients for this email message.</span></span>|  
|<span data-ttu-id="6b5fb-140">BCC</span><span class="sxs-lookup"><span data-stu-id="6b5fb-140">BCC</span></span>|<xref:System.Activities.InArgument%601>\<<xref:System.Net.Mail.MailAddressCollection>>|<span data-ttu-id="6b5fb-141">Collection d’adresses qui contient les destinataires de copie carbone aveugle (BCC) pour ce message électronique.</span><span class="sxs-lookup"><span data-stu-id="6b5fb-141">Address collection that contains the blind carbon copy (BCC) recipients for this email message.</span></span>|  
|<span data-ttu-id="6b5fb-142">Jetons</span><span class="sxs-lookup"><span data-stu-id="6b5fb-142">Tokens</span></span>|<span data-ttu-id="6b5fb-143"><xref:System.Activities.InArgument%601><chaîne iDictionnaire,\<>> de cordes</span><span class="sxs-lookup"><span data-stu-id="6b5fb-143"><xref:System.Activities.InArgument%601><IDictionary\<string, string>></span></span>|<span data-ttu-id="6b5fb-144">Jetons à remplacer dans le corps.</span><span class="sxs-lookup"><span data-stu-id="6b5fb-144">Tokens to replace in the body.</span></span> <span data-ttu-id="6b5fb-145">Cette fonctionnalité permet aux utilisateurs de spécifier certaines valeurs dans le corps qui peuvent être remplacées ultérieurement par les jetons fournis à l’aide de cette propriété.</span><span class="sxs-lookup"><span data-stu-id="6b5fb-145">This feature allows users to specify some values in the body than can be replaced later by the tokens provided using this property.</span></span>|  
|<span data-ttu-id="6b5fb-146">BodyTemplateFilePath</span><span class="sxs-lookup"><span data-stu-id="6b5fb-146">BodyTemplateFilePath</span></span>|<span data-ttu-id="6b5fb-147">String</span><span class="sxs-lookup"><span data-stu-id="6b5fb-147">String</span></span>|<span data-ttu-id="6b5fb-148">Chemin d'accès à un modèle de corps.</span><span class="sxs-lookup"><span data-stu-id="6b5fb-148">Path of a template for the body.</span></span> <span data-ttu-id="6b5fb-149">L'activité `SendMail` copie le contenu de ce fichier dans sa propriété de corps.</span><span class="sxs-lookup"><span data-stu-id="6b5fb-149">The `SendMail` activity copies the contents of this file to its body property.</span></span><br /><br /> <span data-ttu-id="6b5fb-150">Ce modèle peut contenir des jetons qui sont remplacés par le contenu de la propriété des jetons.</span><span class="sxs-lookup"><span data-stu-id="6b5fb-150">The template can contain tokens that are replaced by the contents of the tokens property.</span></span>|  
|<span data-ttu-id="6b5fb-151">TestMailTo</span><span class="sxs-lookup"><span data-stu-id="6b5fb-151">TestMailTo</span></span>|<xref:System.Net.Mail.MailAddress>|<span data-ttu-id="6b5fb-152">Lorsque cette propriété est définie, tous les e-mails sont envoyés à l’adresse spécifiée dans celui-ci.</span><span class="sxs-lookup"><span data-stu-id="6b5fb-152">When this property is set, all emails are sent to the address specified in it.</span></span><br /><br /> <span data-ttu-id="6b5fb-153">Cette propriété n'est pas conçue pour une utilisation lors du test des workflows.</span><span class="sxs-lookup"><span data-stu-id="6b5fb-153">This property is intended to be used when testing workflows.</span></span> <span data-ttu-id="6b5fb-154">Par exemple, lorsque vous voulez vous assurer que tous les e-mails sont envoyés sans les envoyer aux destinataires réels.</span><span class="sxs-lookup"><span data-stu-id="6b5fb-154">For example, when you want to make sure that all emails are sent without sending them to the actual recipients.</span></span>|  
|<span data-ttu-id="6b5fb-155">TestDropPath</span><span class="sxs-lookup"><span data-stu-id="6b5fb-155">TestDropPath</span></span>|<span data-ttu-id="6b5fb-156">String</span><span class="sxs-lookup"><span data-stu-id="6b5fb-156">String</span></span>|<span data-ttu-id="6b5fb-157">Lorsque cette propriété est définie, tous les e-mails sont également enregistrés dans le fichier spécifié.</span><span class="sxs-lookup"><span data-stu-id="6b5fb-157">When this property is set, all emails are also saved in the specified file.</span></span><br /><br /> <span data-ttu-id="6b5fb-158">Cette propriété est destinée à être utilisée lorsque vous testez ou débogagez des flux de travail, pour s’assurer que le format et le contenu des e-mails sortants sont appropriés.</span><span class="sxs-lookup"><span data-stu-id="6b5fb-158">This property is intended to be used when you are testing or debugging workflows, to make sure that the format and contents of the outgoing emails is appropriate.</span></span>|  
  
## <a name="solution-contents"></a><span data-ttu-id="6b5fb-159">Contenu de la solution</span><span class="sxs-lookup"><span data-stu-id="6b5fb-159">Solution Contents</span></span>  
 <span data-ttu-id="6b5fb-160">La solution contient deux projets.</span><span class="sxs-lookup"><span data-stu-id="6b5fb-160">The solution contains two projects.</span></span>  
  
|<span data-ttu-id="6b5fb-161">Projet</span><span class="sxs-lookup"><span data-stu-id="6b5fb-161">Project</span></span>|<span data-ttu-id="6b5fb-162">Description</span><span class="sxs-lookup"><span data-stu-id="6b5fb-162">Description</span></span>|<span data-ttu-id="6b5fb-163">Fichiers importants</span><span class="sxs-lookup"><span data-stu-id="6b5fb-163">Important Files</span></span>|  
|-------------|-----------------|---------------------|  
|<span data-ttu-id="6b5fb-164">SendMail</span><span class="sxs-lookup"><span data-stu-id="6b5fb-164">SendMail</span></span>|<span data-ttu-id="6b5fb-165">Activité SendMail</span><span class="sxs-lookup"><span data-stu-id="6b5fb-165">The SendMail activity</span></span>|<span data-ttu-id="6b5fb-166">1. SendMail.cs : mise en œuvre de l’activité principale</span><span class="sxs-lookup"><span data-stu-id="6b5fb-166">1.  SendMail.cs: implementation for the main activity</span></span><br /><span data-ttu-id="6b5fb-167">2. SendMailDesigner.xaml et SendMailDesigner.xaml.cs: concepteur pour l’activité SendMail</span><span class="sxs-lookup"><span data-stu-id="6b5fb-167">2.  SendMailDesigner.xaml and SendMailDesigner.xaml.cs: designer for the SendMail activity</span></span><br /><span data-ttu-id="6b5fb-168">3. MailTemplateBody.htm: modèle pour l’e-mail à envoyer.</span><span class="sxs-lookup"><span data-stu-id="6b5fb-168">3.  MailTemplateBody.htm: template for the email to be sent out.</span></span>|  
|<span data-ttu-id="6b5fb-169">SendMailTestClient</span><span class="sxs-lookup"><span data-stu-id="6b5fb-169">SendMailTestClient</span></span>|<span data-ttu-id="6b5fb-170">Client pour tester l'activité SendMail.</span><span class="sxs-lookup"><span data-stu-id="6b5fb-170">Client to test the SendMail activity.</span></span>  <span data-ttu-id="6b5fb-171">Ce projet illustre deux façons d'appeler l'activité SendMail : déclarative et par programme.</span><span class="sxs-lookup"><span data-stu-id="6b5fb-171">This project demonstrates two ways of invoking the SendMail activity: declaratively, and programmatically.</span></span>|<span data-ttu-id="6b5fb-172">1. Séquence1.xaml: flux de travail qui invoque l’activité SendMail.</span><span class="sxs-lookup"><span data-stu-id="6b5fb-172">1.  Sequence1.xaml: workflow that invokes the SendMail activity.</span></span><br /><span data-ttu-id="6b5fb-173">2. Program.cs: invoque Séquence1 et crée également un flux de travail programmatiquement qui utilise SendMail.</span><span class="sxs-lookup"><span data-stu-id="6b5fb-173">2.  Program.cs: invokes Sequence1 and also creates a workflow programmatically that uses SendMail.</span></span>|  
  
## <a name="further-configuration-of-the-sendmail-activity"></a><span data-ttu-id="6b5fb-174">Configuration supplémentaire de l'activité SendMail</span><span class="sxs-lookup"><span data-stu-id="6b5fb-174">Further configuration of the SendMail activity</span></span>  
 <span data-ttu-id="6b5fb-175">Bien qu'elle ne soit pas illustrée dans l'exemple, les utilisateurs peuvent effectuer une configuration supplémentaire de l'activité SendMail.</span><span class="sxs-lookup"><span data-stu-id="6b5fb-175">Although not shown in the sample, users can perform addition configuration of the SendMail activity.</span></span> <span data-ttu-id="6b5fb-176">Les trois sections suivantes montrent comment procéder.</span><span class="sxs-lookup"><span data-stu-id="6b5fb-176">The next three sections demonstrate how this is done.</span></span>  
  
### <a name="sending-an-email-using-tokens-specified-in-the-body"></a><span data-ttu-id="6b5fb-177">Envoi d'un message électronique à l'aide de jetons spécifiés dans le corps</span><span class="sxs-lookup"><span data-stu-id="6b5fb-177">Sending an email using tokens specified in the body</span></span>  
 <span data-ttu-id="6b5fb-178">Cet extrait de code montre comment envoyer un message électronique avec des jetons dans le corps.</span><span class="sxs-lookup"><span data-stu-id="6b5fb-178">This code snippet demonstrates how you can send email with tokens in the body.</span></span> <span data-ttu-id="6b5fb-179">Notez la façon dont les jetons sont fournis dans la propriété de corps.</span><span class="sxs-lookup"><span data-stu-id="6b5fb-179">Notice how the tokens are provided in the body property.</span></span> <span data-ttu-id="6b5fb-180">Les valeurs pour ces jetons sont fournies à la propriété de jetons.</span><span class="sxs-lookup"><span data-stu-id="6b5fb-180">Values for those tokens are provided to the tokens property.</span></span>  
  
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
  
### <a name="sending-an-email-using-a-template"></a><span data-ttu-id="6b5fb-181">Envoi d'un message électronique à l'aide d'un modèle</span><span class="sxs-lookup"><span data-stu-id="6b5fb-181">Sending an email using a template</span></span>  
 <span data-ttu-id="6b5fb-182">Cet extrait de code montre comment envoyer un message électronique à l'aide de jetons de modèle dans le corps.</span><span class="sxs-lookup"><span data-stu-id="6b5fb-182">This snippet shows how to send an email using a template tokens in the body.</span></span> <span data-ttu-id="6b5fb-183">Notez que lorsque vous définissez la propriété `BodyTemplateFilePath`, il n'est pas nécessaire de fournir la valeur pour la propriété Body (le contenu du modèle sera copié dans le corps).</span><span class="sxs-lookup"><span data-stu-id="6b5fb-183">Notice that when setting the `BodyTemplateFilePath` property we don’t need to provide the value for Body property (the contents of the template file will be copied to the body).</span></span>  
  
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
  
### <a name="sending-mails-in-testing-mode"></a><span data-ttu-id="6b5fb-184">Envoi de messages électronique en mode Test</span><span class="sxs-lookup"><span data-stu-id="6b5fb-184">Sending Mails in Testing Mode</span></span>  
 <span data-ttu-id="6b5fb-185">Cet extrait de code montre comment définir les deux `TestMailTo` propriétés de test `john.doe@contoso.con` : en définissant tous les messages seront envoyés à (sans égard aux valeurs de To, Cc, Bcc).</span><span class="sxs-lookup"><span data-stu-id="6b5fb-185">This code snippet shows how to set the two testing properties: by setting `TestMailTo` to all messages will be sent to `john.doe@contoso.con` (without regard of the values of To, Cc, Bcc).</span></span> <span data-ttu-id="6b5fb-186">En définissant TestDropPath, tous les messages électroniques sortants seront aussi enregistrés dans le chemin d'accès fourni.</span><span class="sxs-lookup"><span data-stu-id="6b5fb-186">By setting TestDropPath all outgoing emails will be also recorded in the provided path.</span></span> <span data-ttu-id="6b5fb-187">Ces propriétés peuvent être définies indépendamment (elles ne sont pas liées).</span><span class="sxs-lookup"><span data-stu-id="6b5fb-187">These properties can be set independently (they are not related).</span></span>  
  
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
  
## <a name="set-up-instructions"></a><span data-ttu-id="6b5fb-188">Instructions d'installation</span><span class="sxs-lookup"><span data-stu-id="6b5fb-188">Set-Up Instructions</span></span>  
 <span data-ttu-id="6b5fb-189">Vous devez avoir accès à un serveur SMTP pour cet exemple.</span><span class="sxs-lookup"><span data-stu-id="6b5fb-189">Access to a SMTP server is required for this sample.</span></span>  
  
 <span data-ttu-id="6b5fb-190">Pour plus d’informations sur la configuration d’un serveur SMTP, voir les liens suivants.</span><span class="sxs-lookup"><span data-stu-id="6b5fb-190">For more information about setting up a SMTP server, see the following links.</span></span>  
  
- <span data-ttu-id="6b5fb-191">[Configuration du service SMTP (IIS 6.0)](https://docs.microsoft.com/previous-versions/windows/it-pro/windows-server-2003/cc784968(v=ws.10))</span><span class="sxs-lookup"><span data-stu-id="6b5fb-191">[Configuring the SMTP Service (IIS 6.0)](https://docs.microsoft.com/previous-versions/windows/it-pro/windows-server-2003/cc784968(v=ws.10))</span></span>  
  
- <span data-ttu-id="6b5fb-192">[IIS 7.0 : Configuration d'un courrier électronique SMTP](https://docs.microsoft.com/previous-versions/windows/it-pro/windows-server-2008-R2-and-2008/cc772058(v=ws.10))</span><span class="sxs-lookup"><span data-stu-id="6b5fb-192">[IIS 7.0: Configure SMTP E-Mail](https://docs.microsoft.com/previous-versions/windows/it-pro/windows-server-2008-R2-and-2008/cc772058(v=ws.10))</span></span>  
  
- <span data-ttu-id="6b5fb-193">[Procédure : installer le service SMTP](https://docs.microsoft.com/previous-versions/tn-archive/aa997480(v=exchg.65))</span><span class="sxs-lookup"><span data-stu-id="6b5fb-193">[How to Install the SMTP Service](https://docs.microsoft.com/previous-versions/tn-archive/aa997480(v=exchg.65))</span></span>  
  
 <span data-ttu-id="6b5fb-194">Les émulateurs SMTP fournis par des tiers ne sont pas disponibles pour le téléchargement.</span><span class="sxs-lookup"><span data-stu-id="6b5fb-194">SMTP emulators provided by third parties are available for download.</span></span>  
  
##### <a name="to-run-this-sample"></a><span data-ttu-id="6b5fb-195">Pour exécuter l'exemple</span><span class="sxs-lookup"><span data-stu-id="6b5fb-195">To run this sample</span></span>  
  
1. <span data-ttu-id="6b5fb-196">À l’aide de Visual Studio 2010, ouvrez le fichier de solution SendMail.sln.</span><span class="sxs-lookup"><span data-stu-id="6b5fb-196">Using Visual Studio 2010, open the SendMail.sln solution file.</span></span>  
  
2. <span data-ttu-id="6b5fb-197">Vérifiez que vous avez accès à un serveur SMTP valide.</span><span class="sxs-lookup"><span data-stu-id="6b5fb-197">Ensure that you have access to a valid SMTP server.</span></span> <span data-ttu-id="6b5fb-198">Consultez les instructions d'installation.</span><span class="sxs-lookup"><span data-stu-id="6b5fb-198">See the set-up instructions.</span></span>  
  
3. <span data-ttu-id="6b5fb-199">Configurez le programme avec votre adresse serveur, et à partir et à des adresses e-mail.</span><span class="sxs-lookup"><span data-stu-id="6b5fb-199">Configure the program with your server address, and From and To email addresses.</span></span>  
  
     <span data-ttu-id="6b5fb-200">Pour exécuter correctement cet exemple, vous devrez peut-être configurer la valeur des adresses e-mail et de From and To et de l’adresse du serveur SMTP dans Program.cs et dans Sequence.xaml.</span><span class="sxs-lookup"><span data-stu-id="6b5fb-200">To correctly run this sample, you may need to configure the value of From and To email addresses and the address of the SMTP server in  Program.cs and in Sequence.xaml.</span></span> <span data-ttu-id="6b5fb-201">Vous devrez modifier l'adresse à ces deux emplacements car le programme envoie les messages de différentes façons.</span><span class="sxs-lookup"><span data-stu-id="6b5fb-201">You will need to change the address in both locations since the program sends mail in two different ways</span></span>  
  
4. <span data-ttu-id="6b5fb-202">Pour générer la solution, appuyez sur Ctrl+Maj+B.</span><span class="sxs-lookup"><span data-stu-id="6b5fb-202">To build the solution, press CTRL+SHIFT+B.</span></span>  
  
5. <span data-ttu-id="6b5fb-203">Pour exécuter la solution, appuyez sur Ctrl+F5.</span><span class="sxs-lookup"><span data-stu-id="6b5fb-203">To run the solution, press CTRL+F5.</span></span>  
  
> [!IMPORTANT]
> <span data-ttu-id="6b5fb-204">Les exemples peuvent déjà être installés sur votre ordinateur.</span><span class="sxs-lookup"><span data-stu-id="6b5fb-204">The samples may already be installed on your machine.</span></span> <span data-ttu-id="6b5fb-205">Recherchez le répertoire (par défaut) suivant avant de continuer.</span><span class="sxs-lookup"><span data-stu-id="6b5fb-205">Check for the following (default) directory before continuing.</span></span>  
>
> `<InstallDrive>:\WF_WCF_Samples`  
>
> <span data-ttu-id="6b5fb-206">Si ce répertoire n’existe pas, rendez-vous sur [Windows Communication Foundation (WCF) et Windows Workflow Foundation (WF) Samples pour .NET Framework 4 pour](https://www.microsoft.com/download/details.aspx?id=21459) télécharger tous les Windows Communication Foundation (WCF) et [!INCLUDE[wf1](../../../../includes/wf1-md.md)] des échantillons.</span><span class="sxs-lookup"><span data-stu-id="6b5fb-206">If this directory does not exist, go to [Windows Communication Foundation (WCF) and Windows Workflow Foundation (WF) Samples for .NET Framework 4](https://www.microsoft.com/download/details.aspx?id=21459) to download all Windows Communication Foundation (WCF) and [!INCLUDE[wf1](../../../../includes/wf1-md.md)] samples.</span></span> <span data-ttu-id="6b5fb-207">Cet exemple se trouve dans le répertoire suivant.</span><span class="sxs-lookup"><span data-stu-id="6b5fb-207">This sample is located in the following directory.</span></span>  
>
> `<InstallDrive>:\WF_WCF_Samples\WF\Scenario\ActivityLibrary\SendMail`
