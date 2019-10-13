---
title: 'Procédure : héberger un service WCF écrit avec .NET Framework 3.5 dans IIS exécuté sous .NET Framework 4'
ms.date: 03/30/2017
ms.assetid: 9aabc785-068d-4d32-8841-3ef39308d8d6
ms.openlocfilehash: 6a87fd5e3997e9d15810a5efb079da629908f854
ms.sourcegitcommit: 9c3a4f2d3babca8919a1e490a159c1500ba7a844
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 10/12/2019
ms.locfileid: "72291527"
---
# <a name="how-to-host-a-wcf-service-written-with-net-framework-35-in-iis-running-under-net-framework-4"></a><span data-ttu-id="eab33-102">Procédure : héberger un service WCF écrit avec .NET Framework 3.5 dans IIS exécuté sous .NET Framework 4</span><span class="sxs-lookup"><span data-stu-id="eab33-102">How to: Host a WCF Service Written with .NET Framework 3.5 in IIS Running Under .NET Framework 4</span></span>
<span data-ttu-id="eab33-103">Lors de l’hébergement d’un service Windows Communication Foundation (WCF) écrit avec [!INCLUDE[netfx35_long](../../../includes/netfx35-long-md.md)] sur un ordinateur exécutant [!INCLUDE[netfx40_long](../../../includes/netfx40-long-md.md)], vous pouvez obtenir un <xref:System.ServiceModel.ProtocolException> avec le texte suivant.</span><span class="sxs-lookup"><span data-stu-id="eab33-103">When hosting a Windows Communication Foundation (WCF) service written with [!INCLUDE[netfx35_long](../../../includes/netfx35-long-md.md)] on a machine running [!INCLUDE[netfx40_long](../../../includes/netfx40-long-md.md)], you may get a <xref:System.ServiceModel.ProtocolException> with the following text.</span></span>  
  
```output  
Unhandled Exception: System.ServiceModel.ProtocolException: The content type text/html; charset=utf-8 of the response message does not match the content type of the binding (application/soap+xml; charset=utf-8). If using a custom encoder, be sure that the IsContentTypeSupported method is implemented properly. The first 1024 bytes of the response were: '<html>    <head>        <title>The application domain or application pool is currently running version 4.0 or later of the .NET Framework. This can occur if IIS settings have been set to 4.0 or later for this Web application, or if you are using version 4.0 or later of the ASP.NET Web Development Server. The <compilation> element in the Web.config file for this Web application does not contain the required 'targetFrameworkMoniker' attribute for this version of the .NET Framework (for example, '<compilation targetFrameworkMoniker=".NETFramework,Version=v4.0">'). Update the Web.config file with this attribute, or configure the Web application to use a different version of the .NET Framework.</title>...  
```  
  
 <span data-ttu-id="eab33-104">Si vous essayez également d'accéder au fichier .svc du service, vous risquez d'obtenir une page d'erreur avec le texte suivant.</span><span class="sxs-lookup"><span data-stu-id="eab33-104">Or if you try to browse to the service's .svc file you may see an error page with the following text.</span></span>  
  
```output  
The application domain or application pool is currently running version 4.0 or later of the .NET Framework. This can occur if IIS settings have been set to 4.0 or later for this Web application, or if you are using version 4.0 or later of the ASP.NET Web Development Server. The <compilation> element in the Web.config file for this Web application does not contain the required 'targetFrameworkMoniker' attribute for this version of the .NET Framework (for example, '<compilation targetFrameworkMoniker=".NETFramework,Version=v4.0">'). Update the Web.config file with this attribute, or configure the Web application to use a different version of the .NET Framework.  
```  
  
 <span data-ttu-id="eab33-105">Ces erreurs se produisent parce que le domaine d'application, dans lequel s'exécute IIS, exécute le [!INCLUDE[netfx40_short](../../../includes/netfx40-short-md.md)], alors que le service WCF s'attend à fonctionner sous le [!INCLUDE[netfx35_short](../../../includes/netfx35-short-md.md)].</span><span class="sxs-lookup"><span data-stu-id="eab33-105">These errors occur because the application domain IIS is running within is running [!INCLUDE[netfx40_short](../../../includes/netfx40-short-md.md)] and the WCF service is expecting to run under [!INCLUDE[netfx35_short](../../../includes/netfx35-short-md.md)].</span></span> <span data-ttu-id="eab33-106">Cette rubrique explique les modifications nécessaires pour que le service s'exécute.</span><span class="sxs-lookup"><span data-stu-id="eab33-106">This topic explains the modifications required to get the service to run.</span></span>  
  
 <span data-ttu-id="eab33-107">Recherchez ensuite l’élément < `compilers` > et modifiez l’option de fournisseur CompilerVersion pour avoir la valeur 4,0.</span><span class="sxs-lookup"><span data-stu-id="eab33-107">Next find the <`compilers`> element and change the CompilerVersion provider option to have a value of 4.0.</span></span> <span data-ttu-id="eab33-108">Par défaut, il existe deux < `compiler` > sous l’élément < `compilers`.</span><span class="sxs-lookup"><span data-stu-id="eab33-108">By default, there are two <`compiler`> elements under the <`compilers`> element.</span></span> <span data-ttu-id="eab33-109">Vous devez mettre à jour l'option de fournisseur CompilerVersion pour les deux éléments, comme indiqué dans l'exemple suivant.</span><span class="sxs-lookup"><span data-stu-id="eab33-109">You must update the CompilerVersion provider option for both as shown in the following example.</span></span>  
  
```xml  
<system.codedom>  
      <compilers>  
        <compiler language="c#;cs;csharp" extension=".cs" warningLevel="4"  
                  type="Microsoft.CSharp.CSharpCodeProvider, System, Version=2.0.0.0, Culture=neutral, PublicKeyToken=b77a5c561934e089">  
          <providerOption name="CompilerVersion" value="v3.5"/>  
          <providerOption name="WarnAsError" value="false"/>  
        </compiler>  
        <compiler language="vb;vbs;visualbasic;vbscript" extension=".vb" warningLevel="4"  
                  type="Microsoft.VisualBasic.VBCodeProvider, System, Version=2.0.0.0, Culture=neutral, PublicKeyToken=b77a5c561934e089">  
          <providerOption name="CompilerVersion" value="v3.5"/>  
          <providerOption name="OptionInfer" value="true"/>  
          <providerOption name="WarnAsError" value="false"/>  
        </compiler>  
      </compilers>  
    </system.codedom>  
```  
  
### <a name="add-the-required-targetframework-attribute"></a><span data-ttu-id="eab33-110">Ajoutez l'attribut targetFramework nécessaire.</span><span class="sxs-lookup"><span data-stu-id="eab33-110">Add the required targetFramework attribute</span></span>  
  
1. <span data-ttu-id="eab33-111">Ouvrez le fichier Web. config du service et recherchez l’élément < `compilation` >.</span><span class="sxs-lookup"><span data-stu-id="eab33-111">Open the service's Web.config file and look for the <`compilation`> element.</span></span>  
  
2. <span data-ttu-id="eab33-112">Ajoutez l’attribut `targetFramework` à l’élément < `compilation` > comme indiqué dans l’exemple suivant.</span><span class="sxs-lookup"><span data-stu-id="eab33-112">Add the `targetFramework` attribute to the <`compilation`> element as shown in the following example.</span></span>  
  
    ```xml  
    <compilation debug="false"  
            targetFramework="4.0">  
  
            <assemblies>  
              <add assembly="System.Core, Version=3.5.0.0, Culture=neutral, PublicKeyToken=B77A5C561934E089"/>  
              <add assembly="System.Xml.Linq, Version=3.5.0.0, Culture=neutral, PublicKeyToken=B77A5C561934E089"/>  
              <add assembly="System.Web.Extensions, Version=3.5.0.0, Culture=neutral, PublicKeyToken=31BF3856AD364E35"/>  
              <add assembly="System.Data.DataSetExtensions, Version=3.5.0.0, Culture=neutral, PublicKeyToken=B77A5C561934E089"/>  
            </assemblies>  
  
          </compilation>  
    ```  
  
3. <span data-ttu-id="eab33-113">Recherchez l’élément < `compilers` > et modifiez l’option de fournisseur CompilerVersion pour avoir la valeur 4,0.</span><span class="sxs-lookup"><span data-stu-id="eab33-113">Find the <`compilers`> element and change the CompilerVersion provider option to have a value of 4.0.</span></span> <span data-ttu-id="eab33-114">Par défaut, il existe deux < `compiler` > sous l’élément < `compilers`.</span><span class="sxs-lookup"><span data-stu-id="eab33-114">By default, there are two <`compiler`> elements under the <`compilers`> element.</span></span> <span data-ttu-id="eab33-115">Vous devez mettre à jour l'option de fournisseur CompilerVersion pour les deux éléments, comme indiqué dans l'exemple suivant.</span><span class="sxs-lookup"><span data-stu-id="eab33-115">You must update the CompilerVersion provider option for both as shown in the following example.</span></span>  
  
    ```xml  
    <system.codedom>  
          <compilers>  
            <compiler language="c#;cs;csharp" extension=".cs" warningLevel="4"  
                      type="Microsoft.CSharp.CSharpCodeProvider, System, Version=2.0.0.0, Culture=neutral, PublicKeyToken=b77a5c561934e089">  
              <providerOption name="CompilerVersion" value="v3.5"/>  
              <providerOption name="WarnAsError" value="false"/>  
            </compiler>  
            <compiler language="vb;vbs;visualbasic;vbscript" extension=".vb" warningLevel="4"  
                      type="Microsoft.VisualBasic.VBCodeProvider, System, Version=2.0.0.0, Culture=neutral, PublicKeyToken=b77a5c561934e089">  
              <providerOption name="CompilerVersion" value="v3.5"/>  
              <providerOption name="OptionInfer" value="true"/>  
              <providerOption name="WarnAsError" value="false"/>  
            </compiler>  
          </compilers>  
        </system.codedom>  
    ```
