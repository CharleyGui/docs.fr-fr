---
title: Activité personnalisée SendMail
ms.date: 03/30/2017
ms.assetid: 947a9ae6-379c-43a3-9cd5-87f573a5739f
ms.openlocfilehash: 4dca15bfd3798b9282960663bea827f9323a1266
ms.sourcegitcommit: 27a15a55019f6b5f2733961738babe94aec0def3
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 09/15/2020
ms.locfileid: "90547725"
---
# <a name="sendmail-custom-activity"></a><span data-ttu-id="38b81-102">Activité personnalisée SendMail</span><span class="sxs-lookup"><span data-stu-id="38b81-102">SendMail Custom Activity</span></span>
<span data-ttu-id="38b81-103">Cet exemple montre comment créer une activité personnalisée dérivée de <xref:System.Activities.AsyncCodeActivity> pour envoyer du courrier à l'aide de SMTP afin de l'utiliser dans une application de workflow.</span><span class="sxs-lookup"><span data-stu-id="38b81-103">This sample demonstrates how to create a custom activity that derives from <xref:System.Activities.AsyncCodeActivity> to send mail using SMTP for use within a workflow application.</span></span> <span data-ttu-id="38b81-104">L’activité personnalisée utilise les fonctionnalités de <xref:System.Net.Mail.SmtpClient> pour envoyer des courriers électroniques de manière asynchrone et pour envoyer du courrier électronique avec l’authentification.</span><span class="sxs-lookup"><span data-stu-id="38b81-104">The custom activity uses the capabilities of <xref:System.Net.Mail.SmtpClient> to send email asynchronously and to send mail with authentication.</span></span> <span data-ttu-id="38b81-105">Elle fournit aussi certaines fonctionnalités d'utilisateur final telles que le mode Test, le remplacement des jetons, les modèles de fichier et le chemin d'accès de dépôt de test.</span><span class="sxs-lookup"><span data-stu-id="38b81-105">It also provides some end-user features like test mode, token replacement, file templates, and test drop path.</span></span>  
  
 <span data-ttu-id="38b81-106">Le tableau suivant décrit en détail les arguments pour l’activité `SendMail`.</span><span class="sxs-lookup"><span data-stu-id="38b81-106">The following table details the arguments for the `SendMail` activity.</span></span>  
  
|<span data-ttu-id="38b81-107">Name</span><span class="sxs-lookup"><span data-stu-id="38b81-107">Name</span></span>|<span data-ttu-id="38b81-108">Type</span><span class="sxs-lookup"><span data-stu-id="38b81-108">Type</span></span>|<span data-ttu-id="38b81-109">Description</span><span class="sxs-lookup"><span data-stu-id="38b81-109">Description</span></span>|  
|-|-|-|  
|<span data-ttu-id="38b81-110">Host</span><span class="sxs-lookup"><span data-stu-id="38b81-110">Host</span></span>|<span data-ttu-id="38b81-111">String</span><span class="sxs-lookup"><span data-stu-id="38b81-111">String</span></span>|<span data-ttu-id="38b81-112">Adresse du serveur hôte SMTP.</span><span class="sxs-lookup"><span data-stu-id="38b81-112">Address of the SMTP server host.</span></span>|  
|<span data-ttu-id="38b81-113">Port</span><span class="sxs-lookup"><span data-stu-id="38b81-113">Port</span></span>|<span data-ttu-id="38b81-114">String</span><span class="sxs-lookup"><span data-stu-id="38b81-114">String</span></span>|<span data-ttu-id="38b81-115">Port du service SMTP dans l'hôte.</span><span class="sxs-lookup"><span data-stu-id="38b81-115">Port of the SMTP service in the host.</span></span>|  
|<span data-ttu-id="38b81-116">EnableSsl</span><span class="sxs-lookup"><span data-stu-id="38b81-116">EnableSsl</span></span>|<span data-ttu-id="38b81-117">bool</span><span class="sxs-lookup"><span data-stu-id="38b81-117">bool</span></span>|<span data-ttu-id="38b81-118">Indique si <xref:System.Net.Mail.SmtpClient> utilise le protocole SSL (Secure Sockets Layer) pour chiffrer la connexion.</span><span class="sxs-lookup"><span data-stu-id="38b81-118">Specifies whether the <xref:System.Net.Mail.SmtpClient> uses Secure Sockets Layer (SSL) to encrypt the connection.</span></span>|  
|<span data-ttu-id="38b81-119">UserName</span><span class="sxs-lookup"><span data-stu-id="38b81-119">UserName</span></span>|<span data-ttu-id="38b81-120">String</span><span class="sxs-lookup"><span data-stu-id="38b81-120">String</span></span>|<span data-ttu-id="38b81-121">Nom d'utilisateur pour définir les informations d'identification utilisées pour authentifier la propriété <xref:System.Net.Mail.SmtpClient.Credentials%2A> de l'expéditeur.</span><span class="sxs-lookup"><span data-stu-id="38b81-121">Username to set up the credentials to authenticate the sender <xref:System.Net.Mail.SmtpClient.Credentials%2A> property.</span></span>|  
|<span data-ttu-id="38b81-122">Mot de passe</span><span class="sxs-lookup"><span data-stu-id="38b81-122">Password</span></span>|<span data-ttu-id="38b81-123">String</span><span class="sxs-lookup"><span data-stu-id="38b81-123">String</span></span>|<span data-ttu-id="38b81-124">Mot de passe pour définir les informations d'identification utilisées pour authentifier la propriété <xref:System.Net.Mail.SmtpClient.Credentials%2A> de l'expéditeur.</span><span class="sxs-lookup"><span data-stu-id="38b81-124">Password to set up the credentials to authenticate the sender <xref:System.Net.Mail.SmtpClient.Credentials%2A> property.</span></span>|  
|<span data-ttu-id="38b81-125">Objet</span><span class="sxs-lookup"><span data-stu-id="38b81-125">Subject</span></span>|<xref:System.Activities.InArgument%601>\<string>|<span data-ttu-id="38b81-126">Sujet du message.</span><span class="sxs-lookup"><span data-stu-id="38b81-126">Subject of the message.</span></span>|  
|<span data-ttu-id="38b81-127">body</span><span class="sxs-lookup"><span data-stu-id="38b81-127">Body</span></span>|<xref:System.Activities.InArgument%601>\<string>|<span data-ttu-id="38b81-128">Corps du message.</span><span class="sxs-lookup"><span data-stu-id="38b81-128">Body of the message.</span></span>|  
|<span data-ttu-id="38b81-129">Pièces jointes</span><span class="sxs-lookup"><span data-stu-id="38b81-129">Attachments</span></span>|<xref:System.Activities.InArgument%601>\<string>|<span data-ttu-id="38b81-130">Collection de pièces jointes utilisée pour stocker les données jointes à ce message électronique.</span><span class="sxs-lookup"><span data-stu-id="38b81-130">Attachment collection used to store data attached to this email message.</span></span>|  
|<span data-ttu-id="38b81-131">À partir</span><span class="sxs-lookup"><span data-stu-id="38b81-131">From</span></span>|<xref:System.Net.Mail.MailAddress>|<span data-ttu-id="38b81-132">Adresse de l’adresse de ce message électronique.</span><span class="sxs-lookup"><span data-stu-id="38b81-132">From address for this email message.</span></span>|  
|<span data-ttu-id="38b81-133">À</span><span class="sxs-lookup"><span data-stu-id="38b81-133">To</span></span>|<xref:System.Activities.InArgument%601>\<<xref:System.Net.Mail.MailAddressCollection>>|<span data-ttu-id="38b81-134">Collection d’adresses qui contient les destinataires de ce message électronique.</span><span class="sxs-lookup"><span data-stu-id="38b81-134">Address collection that contains the recipients of this email message.</span></span>|  
|<span data-ttu-id="38b81-135">CC</span><span class="sxs-lookup"><span data-stu-id="38b81-135">CC</span></span>|<xref:System.Activities.InArgument%601>\<<xref:System.Net.Mail.MailAddressCollection>>|<span data-ttu-id="38b81-136">Collection d’adresses qui contient les destinataires de copie carbone (CC) pour ce message électronique.</span><span class="sxs-lookup"><span data-stu-id="38b81-136">Address collection that contains the carbon copy (CC) recipients for this email message.</span></span>|  
|<span data-ttu-id="38b81-137">BCC</span><span class="sxs-lookup"><span data-stu-id="38b81-137">BCC</span></span>|<xref:System.Activities.InArgument%601>\<<xref:System.Net.Mail.MailAddressCollection>>|<span data-ttu-id="38b81-138">Collection d’adresses qui contient les destinataires de copie carbone invisible (CCI) pour ce message électronique.</span><span class="sxs-lookup"><span data-stu-id="38b81-138">Address collection that contains the blind carbon copy (BCC) recipients for this email message.</span></span>|  
|<span data-ttu-id="38b81-139">Jetons</span><span class="sxs-lookup"><span data-stu-id="38b81-139">Tokens</span></span>|<span data-ttu-id="38b81-140"><xref:System.Activities.InArgument%601><IDictionary\<string, string>></span><span class="sxs-lookup"><span data-stu-id="38b81-140"><xref:System.Activities.InArgument%601><IDictionary\<string, string>></span></span>|<span data-ttu-id="38b81-141">Jetons à remplacer dans le corps.</span><span class="sxs-lookup"><span data-stu-id="38b81-141">Tokens to replace in the body.</span></span> <span data-ttu-id="38b81-142">Cette fonctionnalité permet aux utilisateurs de spécifier certaines valeurs dans le corps qui peuvent être remplacées ultérieurement par les jetons fournis à l’aide de cette propriété.</span><span class="sxs-lookup"><span data-stu-id="38b81-142">This feature allows users to specify some values in the body than can be replaced later by the tokens provided using this property.</span></span>|  
|<span data-ttu-id="38b81-143">BodyTemplateFilePath</span><span class="sxs-lookup"><span data-stu-id="38b81-143">BodyTemplateFilePath</span></span>|<span data-ttu-id="38b81-144">String</span><span class="sxs-lookup"><span data-stu-id="38b81-144">String</span></span>|<span data-ttu-id="38b81-145">Chemin d'accès à un modèle de corps.</span><span class="sxs-lookup"><span data-stu-id="38b81-145">Path of a template for the body.</span></span> <span data-ttu-id="38b81-146">L'activité `SendMail` copie le contenu de ce fichier dans sa propriété de corps.</span><span class="sxs-lookup"><span data-stu-id="38b81-146">The `SendMail` activity copies the contents of this file to its body property.</span></span><br /><br /> <span data-ttu-id="38b81-147">Ce modèle peut contenir des jetons qui sont remplacés par le contenu de la propriété des jetons.</span><span class="sxs-lookup"><span data-stu-id="38b81-147">The template can contain tokens that are replaced by the contents of the tokens property.</span></span>|  
|<span data-ttu-id="38b81-148">TestMailTo</span><span class="sxs-lookup"><span data-stu-id="38b81-148">TestMailTo</span></span>|<xref:System.Net.Mail.MailAddress>|<span data-ttu-id="38b81-149">Lorsque cette propriété est définie, tous les messages électroniques sont envoyés à l’adresse spécifiée dans celle-ci.</span><span class="sxs-lookup"><span data-stu-id="38b81-149">When this property is set, all emails are sent to the address specified in it.</span></span><br /><br /> <span data-ttu-id="38b81-150">Cette propriété n'est pas conçue pour une utilisation lors du test des workflows.</span><span class="sxs-lookup"><span data-stu-id="38b81-150">This property is intended to be used when testing workflows.</span></span> <span data-ttu-id="38b81-151">Par exemple, lorsque vous souhaitez vous assurer que tous les courriers électroniques sont envoyés sans les envoyer aux destinataires réels.</span><span class="sxs-lookup"><span data-stu-id="38b81-151">For example, when you want to make sure that all emails are sent without sending them to the actual recipients.</span></span>|  
|<span data-ttu-id="38b81-152">TestDropPath</span><span class="sxs-lookup"><span data-stu-id="38b81-152">TestDropPath</span></span>|<span data-ttu-id="38b81-153">String</span><span class="sxs-lookup"><span data-stu-id="38b81-153">String</span></span>|<span data-ttu-id="38b81-154">Lorsque cette propriété est définie, tous les courriers électroniques sont également enregistrés dans le fichier spécifié.</span><span class="sxs-lookup"><span data-stu-id="38b81-154">When this property is set, all emails are also saved in the specified file.</span></span><br /><br /> <span data-ttu-id="38b81-155">Cette propriété est destinée à être utilisée lorsque vous testez ou déboguez des flux de travail pour vous assurer que le format et le contenu des messages sortants sont appropriés.</span><span class="sxs-lookup"><span data-stu-id="38b81-155">This property is intended to be used when you are testing or debugging workflows, to make sure that the format and contents of the outgoing emails is appropriate.</span></span>|  
  
## <a name="solution-contents"></a><span data-ttu-id="38b81-156">Contenu de la solution</span><span class="sxs-lookup"><span data-stu-id="38b81-156">Solution Contents</span></span>  
 <span data-ttu-id="38b81-157">La solution contient deux projets.</span><span class="sxs-lookup"><span data-stu-id="38b81-157">The solution contains two projects.</span></span>  
  
|<span data-ttu-id="38b81-158">Projet</span><span class="sxs-lookup"><span data-stu-id="38b81-158">Project</span></span>|<span data-ttu-id="38b81-159">Description</span><span class="sxs-lookup"><span data-stu-id="38b81-159">Description</span></span>|<span data-ttu-id="38b81-160">Fichiers importants</span><span class="sxs-lookup"><span data-stu-id="38b81-160">Important Files</span></span>|  
|-------------|-----------------|---------------------|  
|<span data-ttu-id="38b81-161">SendMail</span><span class="sxs-lookup"><span data-stu-id="38b81-161">SendMail</span></span>|<span data-ttu-id="38b81-162">Activité SendMail</span><span class="sxs-lookup"><span data-stu-id="38b81-162">The SendMail activity</span></span>|<span data-ttu-id="38b81-163">1. SendMail.cs : implémentation de l’activité principale</span><span class="sxs-lookup"><span data-stu-id="38b81-163">1.  SendMail.cs: implementation for the main activity</span></span><br /><span data-ttu-id="38b81-164">2. SendMailDesigner. xaml et SendMailDesigner.xaml.cs : Designer pour l’activité SendMail</span><span class="sxs-lookup"><span data-stu-id="38b81-164">2.  SendMailDesigner.xaml and SendMailDesigner.xaml.cs: designer for the SendMail activity</span></span><br /><span data-ttu-id="38b81-165">3. MailTemplateBody.htm : modèle de l’e-mail à envoyer.</span><span class="sxs-lookup"><span data-stu-id="38b81-165">3.  MailTemplateBody.htm: template for the email to be sent out.</span></span>|  
|<span data-ttu-id="38b81-166">SendMailTestClient</span><span class="sxs-lookup"><span data-stu-id="38b81-166">SendMailTestClient</span></span>|<span data-ttu-id="38b81-167">Client pour tester l'activité SendMail.</span><span class="sxs-lookup"><span data-stu-id="38b81-167">Client to test the SendMail activity.</span></span>  <span data-ttu-id="38b81-168">Ce projet illustre deux façons d'appeler l'activité SendMail : déclarative et par programme.</span><span class="sxs-lookup"><span data-stu-id="38b81-168">This project demonstrates two ways of invoking the SendMail activity: declaratively, and programmatically.</span></span>|<span data-ttu-id="38b81-169">1. Sequence1. xaml : workflow qui appelle l’activité SendMail.</span><span class="sxs-lookup"><span data-stu-id="38b81-169">1.  Sequence1.xaml: workflow that invokes the SendMail activity.</span></span><br /><span data-ttu-id="38b81-170">2. Program.cs : appelle Sequence1 et crée également un workflow par programme qui utilise SendMail.</span><span class="sxs-lookup"><span data-stu-id="38b81-170">2.  Program.cs: invokes Sequence1 and also creates a workflow programmatically that uses SendMail.</span></span>|  
  
## <a name="further-configuration-of-the-sendmail-activity"></a><span data-ttu-id="38b81-171">Configuration supplémentaire de l'activité SendMail</span><span class="sxs-lookup"><span data-stu-id="38b81-171">Further configuration of the SendMail activity</span></span>  
 <span data-ttu-id="38b81-172">Bien qu'elle ne soit pas illustrée dans l'exemple, les utilisateurs peuvent effectuer une configuration supplémentaire de l'activité SendMail.</span><span class="sxs-lookup"><span data-stu-id="38b81-172">Although not shown in the sample, users can perform addition configuration of the SendMail activity.</span></span> <span data-ttu-id="38b81-173">Les trois sections suivantes montrent comment procéder.</span><span class="sxs-lookup"><span data-stu-id="38b81-173">The next three sections demonstrate how this is done.</span></span>  
  
### <a name="sending-an-email-using-tokens-specified-in-the-body"></a><span data-ttu-id="38b81-174">Envoi d'un message électronique à l'aide de jetons spécifiés dans le corps</span><span class="sxs-lookup"><span data-stu-id="38b81-174">Sending an email using tokens specified in the body</span></span>  
 <span data-ttu-id="38b81-175">Cet extrait de code montre comment envoyer un message électronique avec des jetons dans le corps.</span><span class="sxs-lookup"><span data-stu-id="38b81-175">This code snippet demonstrates how you can send email with tokens in the body.</span></span> <span data-ttu-id="38b81-176">Notez la façon dont les jetons sont fournis dans la propriété de corps.</span><span class="sxs-lookup"><span data-stu-id="38b81-176">Notice how the tokens are provided in the body property.</span></span> <span data-ttu-id="38b81-177">Les valeurs pour ces jetons sont fournies à la propriété de jetons.</span><span class="sxs-lookup"><span data-stu-id="38b81-177">Values for those tokens are provided to the tokens property.</span></span>  
  
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
  
### <a name="sending-an-email-using-a-template"></a><span data-ttu-id="38b81-178">Envoi d'un message électronique à l'aide d'un modèle</span><span class="sxs-lookup"><span data-stu-id="38b81-178">Sending an email using a template</span></span>  
 <span data-ttu-id="38b81-179">Cet extrait de code montre comment envoyer un message électronique à l'aide de jetons de modèle dans le corps.</span><span class="sxs-lookup"><span data-stu-id="38b81-179">This snippet shows how to send an email using a template tokens in the body.</span></span> <span data-ttu-id="38b81-180">Notez que lorsque vous définissez la propriété `BodyTemplateFilePath`, il n'est pas nécessaire de fournir la valeur pour la propriété Body (le contenu du modèle sera copié dans le corps).</span><span class="sxs-lookup"><span data-stu-id="38b81-180">Notice that when setting the `BodyTemplateFilePath` property we don’t need to provide the value for Body property (the contents of the template file will be copied to the body).</span></span>  
  
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
  
### <a name="sending-mails-in-testing-mode"></a><span data-ttu-id="38b81-181">Envoi de messages électronique en mode Test</span><span class="sxs-lookup"><span data-stu-id="38b81-181">Sending Mails in Testing Mode</span></span>  
 <span data-ttu-id="38b81-182">Cet extrait de code montre comment définir les deux propriétés de test : en définissant `TestMailTo` sur tous les messages seront envoyés à `john.doe@contoso.con` (sans tenir compte des valeurs de à, CC, CCI).</span><span class="sxs-lookup"><span data-stu-id="38b81-182">This code snippet shows how to set the two testing properties: by setting `TestMailTo` to all messages will be sent to `john.doe@contoso.con` (without regard of the values of To, Cc, Bcc).</span></span> <span data-ttu-id="38b81-183">En définissant TestDropPath, tous les messages électroniques sortants seront aussi enregistrés dans le chemin d'accès fourni.</span><span class="sxs-lookup"><span data-stu-id="38b81-183">By setting TestDropPath all outgoing emails will be also recorded in the provided path.</span></span> <span data-ttu-id="38b81-184">Ces propriétés peuvent être définies indépendamment (elles ne sont pas liées).</span><span class="sxs-lookup"><span data-stu-id="38b81-184">These properties can be set independently (they are not related).</span></span>  
  
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
  
## <a name="set-up-instructions"></a><span data-ttu-id="38b81-185">Instructions d'installation</span><span class="sxs-lookup"><span data-stu-id="38b81-185">Set-Up Instructions</span></span>  
 <span data-ttu-id="38b81-186">Vous devez avoir accès à un serveur SMTP pour cet exemple.</span><span class="sxs-lookup"><span data-stu-id="38b81-186">Access to a SMTP server is required for this sample.</span></span>  
  
 <span data-ttu-id="38b81-187">Pour plus d’informations sur la configuration d’un serveur SMTP, consultez les liens suivants.</span><span class="sxs-lookup"><span data-stu-id="38b81-187">For more information about setting up a SMTP server, see the following links.</span></span>  
  
- <span data-ttu-id="38b81-188">[Configuration du service SMTP (IIS 6.0)](/previous-versions/windows/it-pro/windows-server-2003/cc784968(v=ws.10))</span><span class="sxs-lookup"><span data-stu-id="38b81-188">[Configuring the SMTP Service (IIS 6.0)](/previous-versions/windows/it-pro/windows-server-2003/cc784968(v=ws.10))</span></span>  
  
- <span data-ttu-id="38b81-189">[IIS 7.0 : Configuration d'un courrier électronique SMTP](/previous-versions/windows/it-pro/windows-server-2008-R2-and-2008/cc772058(v=ws.10))</span><span class="sxs-lookup"><span data-stu-id="38b81-189">[IIS 7.0: Configure SMTP E-Mail](/previous-versions/windows/it-pro/windows-server-2008-R2-and-2008/cc772058(v=ws.10))</span></span>  
  
- <span data-ttu-id="38b81-190">[Procédure : installer le service SMTP](/previous-versions/tn-archive/aa997480(v=exchg.65))</span><span class="sxs-lookup"><span data-stu-id="38b81-190">[How to Install the SMTP Service](/previous-versions/tn-archive/aa997480(v=exchg.65))</span></span>  
  
 <span data-ttu-id="38b81-191">Les émulateurs SMTP fournis par des tiers ne sont pas disponibles pour le téléchargement.</span><span class="sxs-lookup"><span data-stu-id="38b81-191">SMTP emulators provided by third parties are available for download.</span></span>  
  
##### <a name="to-run-this-sample"></a><span data-ttu-id="38b81-192">Pour exécuter l'exemple</span><span class="sxs-lookup"><span data-stu-id="38b81-192">To run this sample</span></span>  
  
1. <span data-ttu-id="38b81-193">À l’aide de Visual Studio 2010, ouvrez le fichier solution SendMail. sln.</span><span class="sxs-lookup"><span data-stu-id="38b81-193">Using Visual Studio 2010, open the SendMail.sln solution file.</span></span>  
  
2. <span data-ttu-id="38b81-194">Vérifiez que vous avez accès à un serveur SMTP valide.</span><span class="sxs-lookup"><span data-stu-id="38b81-194">Ensure that you have access to a valid SMTP server.</span></span> <span data-ttu-id="38b81-195">Consultez les instructions d'installation.</span><span class="sxs-lookup"><span data-stu-id="38b81-195">See the set-up instructions.</span></span>  
  
3. <span data-ttu-id="38b81-196">Configurez le programme avec l’adresse de votre serveur et les adresses de messagerie de et à.</span><span class="sxs-lookup"><span data-stu-id="38b81-196">Configure the program with your server address, and From and To email addresses.</span></span>  
  
     <span data-ttu-id="38b81-197">Pour exécuter correctement cet exemple, vous devrez peut-être configurer la valeur de et vers les adresses de messagerie et l’adresse du serveur SMTP dans Program.cs et dans Sequence. Xaml.</span><span class="sxs-lookup"><span data-stu-id="38b81-197">To correctly run this sample, you may need to configure the value of From and To email addresses and the address of the SMTP server in  Program.cs and in Sequence.xaml.</span></span> <span data-ttu-id="38b81-198">Vous devrez modifier l'adresse à ces deux emplacements car le programme envoie les messages de différentes façons.</span><span class="sxs-lookup"><span data-stu-id="38b81-198">You will need to change the address in both locations since the program sends mail in two different ways</span></span>  
  
4. <span data-ttu-id="38b81-199">Pour générer la solution, appuyez sur Ctrl+Maj+B.</span><span class="sxs-lookup"><span data-stu-id="38b81-199">To build the solution, press CTRL+SHIFT+B.</span></span>  
  
5. <span data-ttu-id="38b81-200">Pour exécuter la solution, appuyez sur Ctrl+F5.</span><span class="sxs-lookup"><span data-stu-id="38b81-200">To run the solution, press CTRL+F5.</span></span>  
  
> [!IMPORTANT]
> <span data-ttu-id="38b81-201">Les exemples peuvent déjà être installés sur votre ordinateur.</span><span class="sxs-lookup"><span data-stu-id="38b81-201">The samples may already be installed on your machine.</span></span> <span data-ttu-id="38b81-202">Recherchez le répertoire (par défaut) suivant avant de continuer.</span><span class="sxs-lookup"><span data-stu-id="38b81-202">Check for the following (default) directory before continuing.</span></span>  
>
> `<InstallDrive>:\WF_WCF_Samples`  
>
> <span data-ttu-id="38b81-203">Si ce répertoire n’existe pas, accédez à [Windows Communication Foundation (WCF) et Windows Workflow Foundation (WF) exemples pour .NET Framework 4](https://www.microsoft.com/download/details.aspx?id=21459) pour télécharger tous les exemples Windows Communication Foundation (WCF) et [!INCLUDE[wf1](../../../../includes/wf1-md.md)] .</span><span class="sxs-lookup"><span data-stu-id="38b81-203">If this directory does not exist, go to [Windows Communication Foundation (WCF) and Windows Workflow Foundation (WF) Samples for .NET Framework 4](https://www.microsoft.com/download/details.aspx?id=21459) to download all Windows Communication Foundation (WCF) and [!INCLUDE[wf1](../../../../includes/wf1-md.md)] samples.</span></span> <span data-ttu-id="38b81-204">Cet exemple se trouve dans le répertoire suivant.</span><span class="sxs-lookup"><span data-stu-id="38b81-204">This sample is located in the following directory.</span></span>  
>
> `<InstallDrive>:\WF_WCF_Samples\WF\Scenario\ActivityLibrary\SendMail`
