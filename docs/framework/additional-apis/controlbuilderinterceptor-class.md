---
title: Classe ControlBuilderInterceptor
ms.date: 08/11/2020
api_name:
- System.Web.Compilation.ControlBuilderInterceptor
api_location:
- System.Web.dll
api_type:
- Assembly
topic_type:
- apiref
ms.openlocfilehash: 0cd7409deb9cb84783cfa70600999fa4b2a2d2e2
ms.sourcegitcommit: d337df55f83325918cbbd095eb573400bea49064
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 08/13/2020
ms.locfileid: "88187988"
---
# <a name="controlbuilderinterceptor-class"></a><span data-ttu-id="65f21-102">Classe ControlBuilderInterceptor</span><span class="sxs-lookup"><span data-stu-id="65f21-102">ControlBuilderInterceptor class</span></span>

<span data-ttu-id="65f21-103">La `ControlBuilderInterceptor` classe permet de personnaliser ou de contrôler le processus de compilation.</span><span class="sxs-lookup"><span data-stu-id="65f21-103">The `ControlBuilderInterceptor` class allows the compilation process to be customized or controlled.</span></span>

## <a name="syntax"></a><span data-ttu-id="65f21-104">Syntaxe</span><span class="sxs-lookup"><span data-stu-id="65f21-104">Syntax</span></span>

```csharp
internal class ControlBuilderInterceptor
```

> [!WARNING]
> <span data-ttu-id="65f21-105">La `ControlBuilderInterceptor` classe est interne et n’est pas destinée à être utilisée directement dans votre code.</span><span class="sxs-lookup"><span data-stu-id="65f21-105">The `ControlBuilderInterceptor` class is internal and is not meant to be used directly in your code.</span></span>
>
> <span data-ttu-id="65f21-106">Comme décrit dans la section Notes, l’existence de ce type peut être vérifiée pour déterminer si la prise en charge du type d’intercepteur est présente.</span><span class="sxs-lookup"><span data-stu-id="65f21-106">As described in the Remarks section, the existence of this type can be checked to determine whether interceptor type support is present.</span></span> <span data-ttu-id="65f21-107">Microsoft ne prend en charge aucune autre utilisation de cette classe dans une application de production, dans toutes les circonstances.</span><span class="sxs-lookup"><span data-stu-id="65f21-107">Microsoft does not support any other use of this class in a production application under any circumstance.</span></span>

## <a name="remarks"></a><span data-ttu-id="65f21-108">Notes</span><span class="sxs-lookup"><span data-stu-id="65f21-108">Remarks</span></span>

<span data-ttu-id="65f21-109">Dans .NET Framework 2,0 et .NET Framework 3,5, les mises à jour d' [août 2020](https://portal.msrc.microsoft.com/security-guidance/releasenotedetail/2020-Aug) ajoutent la prise en charge de l’utilisation d’un type d’intercepteur pour personnaliser ou contrôler le processus de compilation.</span><span class="sxs-lookup"><span data-stu-id="65f21-109">In .NET Framework 2.0 and .NET Framework 3.5, the [August 2020](https://portal.msrc.microsoft.com/security-guidance/releasenotedetail/2020-Aug) updates added support for using an interceptor type to customize or control the compilation process.</span></span> <span data-ttu-id="65f21-110">Vous pouvez déterminer si cette prise en charge est présente en utilisant <xref:System.Type.GetType?displayProperty=nameWithType> pour vérifier l’existence du `ControlBuilderInterceptor` type, comme illustré dans le code suivant.</span><span class="sxs-lookup"><span data-stu-id="65f21-110">You can determine whether this support is present by using <xref:System.Type.GetType?displayProperty=nameWithType> to check the existence of the `ControlBuilderInterceptor` type, as demonstrated in the following code.</span></span>

```csharp
Type type = Type.GetType("System.Web.Compilation.ControlBuilderInterceptor, System.Web, Version=2.0.0.0, Culture=neutral, PublicKeyToken=b03f5f7f11d50a3a");
```

<span data-ttu-id="65f21-111">Si la valeur de retour n’est pas null, la prise en charge de l’intercepteur est présente.</span><span class="sxs-lookup"><span data-stu-id="65f21-111">If the return value is non-null, then interceptor support is present.</span></span> <span data-ttu-id="65f21-112">Si la valeur de retour est `null` , ou si une exception est levée, les mises à jour du 2020 d’août n’ont pas été installées et la prise en charge de l’intercepteur est absente.</span><span class="sxs-lookup"><span data-stu-id="65f21-112">If the return value is `null`, or if an exception is thrown, then the August 2020 updates have not been installed, and interceptor support is absent.</span></span>

<span data-ttu-id="65f21-113">Si la prise en charge de l’intercepteur est présente, vous pouvez écrire et inscrire un type d’intercepteur qui interagit avec le processus de compilation exactement de la même façon que <xref:System.Web.Compilation.ControlBuilderInterceptor> dans les versions ultérieures de .NET Framework.</span><span class="sxs-lookup"><span data-stu-id="65f21-113">If interceptor support is present, you can write and register an interceptor type that will interact with the compilation process in exactly the same way that <xref:System.Web.Compilation.ControlBuilderInterceptor> does on later versions of .NET Framework.</span></span> <span data-ttu-id="65f21-114">Dans .NET Framework 2,0 et .NET Framework 3,5, le type d’intercepteur peut être n’importe quelle classe qui répond aux exigences suivantes :</span><span class="sxs-lookup"><span data-stu-id="65f21-114">In .NET Framework 2.0 and .NET Framework 3.5, the interceptor type can be any class that meets the following requirements:</span></span>

* <span data-ttu-id="65f21-115">A un constructeur sans paramètre public.</span><span class="sxs-lookup"><span data-stu-id="65f21-115">Has a public, parameterless constructor.</span></span>
* <span data-ttu-id="65f21-116">A des méthodes publiques et non statiques nommées `PreControlBuilderInit` et ayant `OnProcessGeneratedCode` la même signature et la même sémantique que les <xref:System.Web.Compilation.ControlBuilderInterceptor.PreControlBuilderInit(System.Web.UI.ControlBuilder,System.Web.UI.TemplateParser,System.Web.UI.ControlBuilder,System.Type,System.String,System.String,System.Collections.IDictionary,System.Collections.IDictionary)> <xref:System.Web.Compilation.ControlBuilderInterceptor.OnProcessGeneratedCode(System.Web.UI.ControlBuilder,System.CodeDom.CodeCompileUnit,System.CodeDom.CodeTypeDeclaration,System.CodeDom.CodeTypeDeclaration,System.CodeDom.CodeMemberMethod,System.CodeDom.CodeMemberMethod,System.Collections.IDictionary)> méthodes et, qui existent dans les versions ultérieures de .NET Framework.</span><span class="sxs-lookup"><span data-stu-id="65f21-116">Has public, non-static methods named `PreControlBuilderInit` and `OnProcessGeneratedCode` that have the same signature and semantics as the <xref:System.Web.Compilation.ControlBuilderInterceptor.PreControlBuilderInit(System.Web.UI.ControlBuilder,System.Web.UI.TemplateParser,System.Web.UI.ControlBuilder,System.Type,System.String,System.String,System.Collections.IDictionary,System.Collections.IDictionary)> and <xref:System.Web.Compilation.ControlBuilderInterceptor.OnProcessGeneratedCode(System.Web.UI.ControlBuilder,System.CodeDom.CodeCompileUnit,System.CodeDom.CodeTypeDeclaration,System.CodeDom.CodeTypeDeclaration,System.CodeDom.CodeMemberMethod,System.CodeDom.CodeMemberMethod,System.Collections.IDictionary)> methods, which exist in later versions of .NET Framework.</span></span>

<span data-ttu-id="65f21-117">Inscrivez le type d’intercepteur à l’aide `aspnet:20ControlBuilderInterceptor` de la clé dans les paramètres d’application ASP.net ( `<appSettings>` ).</span><span class="sxs-lookup"><span data-stu-id="65f21-117">Register the interceptor type by using the `aspnet:20ControlBuilderInterceptor` key in ASP.NET application settings (`<appSettings>`).</span></span> <span data-ttu-id="65f21-118">Ce paramètre d’application doit être indiqué dans le fichier de *web.config* de votre ordinateur ou de votre application.</span><span class="sxs-lookup"><span data-stu-id="65f21-118">This application setting must be listed in your computer or application *web.config* file.</span></span> <span data-ttu-id="65f21-119">Spécifiez le type d’intercepteur à l’aide de son nom de type qualifié d’assembly.</span><span class="sxs-lookup"><span data-stu-id="65f21-119">Specify the interceptor type by using its assembly-qualified type name.</span></span> <span data-ttu-id="65f21-120">L’exemple suivant montre comment inscrire un type d’intercepteur nommé `Fabrikam.Interceptor` .</span><span class="sxs-lookup"><span data-stu-id="65f21-120">The following example shows how to register an interceptor type named `Fabrikam.Interceptor`.</span></span>

```xml
<configuration>
  ...
  <appSettings>
    ...
    <add key="aspnet:20ControlBuilderInterceptor"
         value="Fabrikam.Interceptor, Fabrikam, Version=1.0.0.0, Culture=neutral, PublicKeyToken=2b3831f2f2b744f7" />
  </appSettings>
</configuration>
```

<span data-ttu-id="65f21-121">Pour récupérer le nom qualifié d’assembly d’un type, utilisez la <xref:System.Type.AssemblyQualifiedName?displayProperty=nameWithType> propriété, comme illustré dans le code suivant.</span><span class="sxs-lookup"><span data-stu-id="65f21-121">To retrieve the assembly-qualified name of a type, use the <xref:System.Type.AssemblyQualifiedName?displayProperty=nameWithType> property, as demonstrated in the following code.</span></span>

```csharp
string assemblyQualifiedName = typeof(Fabrikam.Interceptor).AssemblyQualifiedName;
```

<span data-ttu-id="65f21-122">Lorsque la prise en charge de l’intercepteur est présente, le processus de compilation interagit avec le type répertorié de la manière décrite ci-dessus.</span><span class="sxs-lookup"><span data-stu-id="65f21-122">When interceptor support is present, the compilation process interacts with the listed type in the manner described above.</span></span> <span data-ttu-id="65f21-123">Lorsque la prise en charge de l’intercepteur est absente, le paramètre d’application est ignoré et n’a aucun effet.</span><span class="sxs-lookup"><span data-stu-id="65f21-123">When interceptor support is absent, the application setting is ignored and has no effect.</span></span>

## <a name="requirements"></a><span data-ttu-id="65f21-124">Configuration requise</span><span class="sxs-lookup"><span data-stu-id="65f21-124">Requirements</span></span>

<span data-ttu-id="65f21-125">**Espace de noms :** System. Web. Compilation</span><span class="sxs-lookup"><span data-stu-id="65f21-125">**Namespace:** System.Web.Compilation</span></span>

<span data-ttu-id="65f21-126">**Assembly :** System. Web (en System.Web.dll)</span><span class="sxs-lookup"><span data-stu-id="65f21-126">**Assembly:** System.Web (in System.Web.dll)</span></span>

<span data-ttu-id="65f21-127">**Versions de .NET Framework :** 3,5, 2,0</span><span class="sxs-lookup"><span data-stu-id="65f21-127">**.NET Framework versions:** 3.5, 2.0</span></span>
