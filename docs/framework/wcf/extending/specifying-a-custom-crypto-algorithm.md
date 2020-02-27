---
title: Spécification d'un algorithme de chiffrement personnalisé
ms.date: 03/30/2017
ms.assetid: d662a305-8e09-451d-9a59-b0f12b012f1d
ms.openlocfilehash: 0bfa6c46f4db1171eb314625e36c267000a0ec12
ms.sourcegitcommit: 44a7cd8687f227fc6db3211ccf4783dc20235e51
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 02/26/2020
ms.locfileid: "77628681"
---
# <a name="specifying-a-custom-crypto-algorithm"></a><span data-ttu-id="bfee2-102">Spécification d'un algorithme de chiffrement personnalisé</span><span class="sxs-lookup"><span data-stu-id="bfee2-102">Specifying a Custom Crypto Algorithm</span></span>
<span data-ttu-id="bfee2-103">WCF vous permet de spécifier un algorithme de chiffrement personnalité pour le chiffrement des données ou le calcul de signatures numériques.</span><span class="sxs-lookup"><span data-stu-id="bfee2-103">WCF allows you to specify a custom crypto algorithm to use when encrypting data or computing digital signatures.</span></span> <span data-ttu-id="bfee2-104">Voici les étapes qui permettent d'effectuer cette opération :</span><span class="sxs-lookup"><span data-stu-id="bfee2-104">This is done by the following steps:</span></span>  
  
1. <span data-ttu-id="bfee2-105">Dériver une classe de <xref:System.ServiceModel.Security.SecurityAlgorithmSuite></span><span class="sxs-lookup"><span data-stu-id="bfee2-105">Derive a class from <xref:System.ServiceModel.Security.SecurityAlgorithmSuite></span></span>  
  
2. <span data-ttu-id="bfee2-106">Enregistrer l'algorithme</span><span class="sxs-lookup"><span data-stu-id="bfee2-106">Register the algorithm</span></span>  
  
3. <span data-ttu-id="bfee2-107">Configurez la liaison avec la classe dérivée <xref:System.ServiceModel.Security.SecurityAlgorithmSuite>.</span><span class="sxs-lookup"><span data-stu-id="bfee2-107">Configure the binding with the <xref:System.ServiceModel.Security.SecurityAlgorithmSuite>-derived class.</span></span>  
  
## <a name="derive-a-class-from-securityalgorithmsuite"></a><span data-ttu-id="bfee2-108">Dériver une classe de SecurityAlgorithmSuite</span><span class="sxs-lookup"><span data-stu-id="bfee2-108">Derive a class from SecurityAlgorithmSuite</span></span>  
 <span data-ttu-id="bfee2-109">La classe <xref:System.ServiceModel.Security.SecurityAlgorithmSuite> est une classe de base abstraite qui vous permet de spécifier l'algorithme à utiliser pour plusieurs opérations liées à la sécurité.</span><span class="sxs-lookup"><span data-stu-id="bfee2-109">The <xref:System.ServiceModel.Security.SecurityAlgorithmSuite> is an abstract base class that allows you to specify the algorithm to use when performing various security related operations.</span></span> <span data-ttu-id="bfee2-110">Par exemple, calculer un hachage pour une signature numérique ou chiffrer un message.</span><span class="sxs-lookup"><span data-stu-id="bfee2-110">For example, computing a hash for a digital signature or encrypting a message.</span></span> <span data-ttu-id="bfee2-111">Le code suivant montre comment dériver une classe à partir de <xref:System.ServiceModel.Security.SecurityAlgorithmSuite> :</span><span class="sxs-lookup"><span data-stu-id="bfee2-111">The following code shows how to derive a class from <xref:System.ServiceModel.Security.SecurityAlgorithmSuite>:</span></span>  
  
```csharp  
public class MyCustomAlgorithmSuite : SecurityAlgorithmSuite  
    {  
        public override string DefaultAsymmetricKeyWrapAlgorithm  
        {  
            get { return SecurityAlgorithms.RsaOaepKeyWrap; }  
        }  
  
        public override string DefaultAsymmetricSignatureAlgorithm  
        {  
            get { return SecurityAlgorithms.RsaSha1Signature; }  
        }  
  
        public override string DefaultCanonicalizationAlgorithm  
        {  
            get { return SecurityAlgorithms.ExclusiveC14n; ; }  
        }  
  
        public override string DefaultDigestAlgorithm  
        {  
            get { return SecurityAlgorithms.MyCustomHashAlgorithm; }  
        }  
  
        public override string DefaultEncryptionAlgorithm  
        {  
            get { return SecurityAlgorithms.Aes128Encryption; }  
        }  
  
        public override int DefaultEncryptionKeyDerivationLength  
        {  
            get { return 128; }  
        }  
  
        public override int DefaultSignatureKeyDerivationLength  
        {  
            get { return 128; }  
        }  
  
        public override int DefaultSymmetricKeyLength  
        {  
            get { return 128; }  
        }  
  
        public override string DefaultSymmetricKeyWrapAlgorithm  
        {  
            get { return SecurityAlgorithms.Aes128Encryption; }  
        }  
  
        public override string DefaultSymmetricSignatureAlgorithm  
        {  
            get { return SecurityAlgorithms.HmacSha1Signature; }  
        }  
  
        public override bool IsAsymmetricKeyLengthSupported(int length)  
        {  
            return length >= 1024 && length <= 4096;  
        }  
  
        public override bool IsSymmetricKeyLengthSupported(int length)  
        {  
            return length >= 128 && length <= 256;  
        }  
    }  
```  
  
## <a name="register-the-custom-algorithm"></a><span data-ttu-id="bfee2-112">Enregistrer l'algorithme personnalisé</span><span class="sxs-lookup"><span data-stu-id="bfee2-112">Register the Custom Algorithm</span></span>  
 <span data-ttu-id="bfee2-113">L'enregistrement peut être effectué dans un fichier de configuration ou en code impératif.</span><span class="sxs-lookup"><span data-stu-id="bfee2-113">Registration can be done in a configuration file or in imperative code.</span></span> <span data-ttu-id="bfee2-114">L'enregistrement d'un algorithme personnalisé s'effectue en créant un mappage entre une classe qui implémente un fournisseur de service de chiffrement et un alias.</span><span class="sxs-lookup"><span data-stu-id="bfee2-114">Registering a custom algorithm is done by creating a mapping between a class that implements a crypto service provider and an alias.</span></span> <span data-ttu-id="bfee2-115">L’alias est ensuite mappé sur un URI qui est utilisé pour spécifier l’algorithme dans la liaison du service WCF.</span><span class="sxs-lookup"><span data-stu-id="bfee2-115">The alias is then mapped to a URI which is used when specifying the algorithm in the WCF service’s binding.</span></span> <span data-ttu-id="bfee2-116">L'extrait de configuration suivant illustre la méthode d'enregistrement d'un algorithme personnalisé :</span><span class="sxs-lookup"><span data-stu-id="bfee2-116">The following configuration snippet illustrates how to register a custom algorithm in config:</span></span>  
  
```xml  
<configuration>  
   <mscorlib>  
      <cryptographySettings>  
         <cryptoNameMapping>  
           <cryptoClasses>  
              <cryptoClass SHA256CSP="System.Security.Cryptography.SHA256CryptoServiceProvider, System.Core, Version=3.5.0.0, Culture=neutral, PublicKeyToken=b77a5c561934e089" />  
           </cryptoClasses>  
           <nameEntry name="http://constoso.com/CustomAlgorithms/CustomHashAlgorithm"  
              class="SHA256CSP" />  
           </cryptoNameMapping>  
        </cryptographySettings>  
    </mscorlib>  
</configuration>  
```  
  
 <span data-ttu-id="bfee2-117">La section sous l’élément <`cryptoClasses`> crée le mappage entre SHA256CryptoServiceProvider et l’alias « SHA256CSP ».</span><span class="sxs-lookup"><span data-stu-id="bfee2-117">The section under the <`cryptoClasses`> element creates the mapping between the SHA256CryptoServiceProvider and the alias "SHA256CSP".</span></span> <span data-ttu-id="bfee2-118">L’élément <`nameEntry`> crée le mappage entre l’alias « SHA256CSP » et l’URL spécifiée `http://constoso.com/CustomAlgorithms/CustomHashAlgorithm`.</span><span class="sxs-lookup"><span data-stu-id="bfee2-118">The <`nameEntry`> element creates the mapping between the "SHA256CSP" alias and the specified URL `http://constoso.com/CustomAlgorithms/CustomHashAlgorithm`.</span></span>  
  
 <span data-ttu-id="bfee2-119">Pour enregistrer l'algorithme personnalisé en code, utilisez la méthode <xref:System.Security.Cryptography.CryptoConfig.AddAlgorithm(System.Type,System.String[])>.</span><span class="sxs-lookup"><span data-stu-id="bfee2-119">To register the custom algorithm in code use the <xref:System.Security.Cryptography.CryptoConfig.AddAlgorithm(System.Type,System.String[])> method.</span></span> <span data-ttu-id="bfee2-120">Cette méthode crée ces deux mappages.</span><span class="sxs-lookup"><span data-stu-id="bfee2-120">This method creates both mappings.</span></span> <span data-ttu-id="bfee2-121">L'exemple suivant illustre l'appel de cette méthode :</span><span class="sxs-lookup"><span data-stu-id="bfee2-121">The following example shows how to call this method:</span></span>  
  
```csharp
// Register the custom URI string defined for the hashAlgorithm in MyCustomAlgorithmSuite class to create the   
// SHA256CryptoServiceProvider hash algorithm object.  
CryptoConfig.AddAlgorithm(typeof(SHA256CryptoServiceProvider), "http://constoso.com/CustomAlgorithms/CustomHashAlgorithm");  
```  
  
## <a name="configure-the-binding"></a><span data-ttu-id="bfee2-122">Configurer la liaison</span><span class="sxs-lookup"><span data-stu-id="bfee2-122">Configure the Binding</span></span>  
 <span data-ttu-id="bfee2-123">Vous pouvez configurer la liaison en spécifiant la classe personnalisée dérivée de <xref:System.ServiceModel.Security.SecurityAlgorithmSuite> dans les paramètres de liaison, comme indiqué dans l’extrait de code suivant :</span><span class="sxs-lookup"><span data-stu-id="bfee2-123">You configure the binding by specifying the custom <xref:System.ServiceModel.Security.SecurityAlgorithmSuite>-derived class in the binding settings as shown in the following code snippet:</span></span>  
  
```csharp  
WSHttpBinding binding = new WSHttpBinding();  
            binding.Security.Message.AlgorithmSuite = new MyCustomAlgorithmSuite();  
```  
  
 <span data-ttu-id="bfee2-124">Pour obtenir un exemple de code complet, consultez l’exemple [agilité de chiffrement dans la sécurité WCF](../samples/cryptographic-agility-in-wcf-security.md) .</span><span class="sxs-lookup"><span data-stu-id="bfee2-124">For a complete code example, see the [Cryptographic Agility in WCF Security](../samples/cryptographic-agility-in-wcf-security.md) sample.</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="bfee2-125">Voir aussi</span><span class="sxs-lookup"><span data-stu-id="bfee2-125">See also</span></span>

- [<span data-ttu-id="bfee2-126">Sécurisation des services et des clients</span><span class="sxs-lookup"><span data-stu-id="bfee2-126">Securing Services and Clients</span></span>](../feature-details/securing-services-and-clients.md)
- [<span data-ttu-id="bfee2-127">Sécurisation de services</span><span class="sxs-lookup"><span data-stu-id="bfee2-127">Securing Services</span></span>](../securing-services.md)
- [<span data-ttu-id="bfee2-128">Présentation de la sécurité</span><span class="sxs-lookup"><span data-stu-id="bfee2-128">Security Overview</span></span>](../feature-details/security-overview.md)
- [<span data-ttu-id="bfee2-129">Concepts relatifs à la sécurité</span><span class="sxs-lookup"><span data-stu-id="bfee2-129">Security Concepts</span></span>](../feature-details/security-concepts.md)
