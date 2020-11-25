---
title: IDENTITY_ATTRIBUTE_BLOB, structure
ms.date: 03/30/2017
dev_langs:
- cpp
api_name:
- IDENTITY_ATTRIBUTE_BLOB
api_location:
- fusion.dll
api_type:
- COM
f1_keywords:
- IDENTITY_ATTRIBUTE_BLOB
helpviewer_keywords:
- IDENTITY_ATTRIBUTE_BLOB structure [.NET Framework fusion]
ms.assetid: af14ae5f-d226-47dd-ba90-8fc6e6605d4d
topic_type:
- apiref
ms.openlocfilehash: 9a59e70257064220e8138f9d267a815fcdbf3929
ms.sourcegitcommit: d8020797a6657d0fbbdff362b80300815f682f94
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 11/24/2020
ms.locfileid: "95729029"
---
# <a name="identity_attribute_blob-structure"></a><span data-ttu-id="3dda8-102">IDENTITY_ATTRIBUTE_BLOB, structure</span><span class="sxs-lookup"><span data-stu-id="3dda8-102">IDENTITY_ATTRIBUTE_BLOB Structure</span></span>

<span data-ttu-id="3dda8-103">Contient des informations sur un attribut unique dans un assembly et se compose de trois `DWORD` s.</span><span class="sxs-lookup"><span data-stu-id="3dda8-103">Contains information about a single attribute in an assembly, and consists of three `DWORD`s.</span></span> <span data-ttu-id="3dda8-104">Chaque `DWORD` est un offset dans une mémoire tampon de caractères produite par la `CurrentIntoBuffer` méthode de l’interface [IEnumIDENTITY_ATTRIBUTE](ienumidentity-attribute-interface.md)</span><span class="sxs-lookup"><span data-stu-id="3dda8-104">Each `DWORD` is an offset into a character buffer produced by the `CurrentIntoBuffer` method of the [IEnumIDENTITY_ATTRIBUTE](ienumidentity-attribute-interface.md) interface</span></span>  
  
## <a name="syntax"></a><span data-ttu-id="3dda8-105">Syntaxe</span><span class="sxs-lookup"><span data-stu-id="3dda8-105">Syntax</span></span>  
  
```cpp  
typedef struct _IDENTITY_ATTRIBUTE_BLOB {  
    DWORD  ofsNamespace;  
    DWORD  ofsName;  
    DWORD  ofsValue;  
}   IDENTITY_ATTRIBUTE_BLOB;  
```  
  
## <a name="members"></a><span data-ttu-id="3dda8-106">Membres</span><span class="sxs-lookup"><span data-stu-id="3dda8-106">Members</span></span>  
  
|<span data-ttu-id="3dda8-107">Membre</span><span class="sxs-lookup"><span data-stu-id="3dda8-107">Member</span></span>|<span data-ttu-id="3dda8-108">Description</span><span class="sxs-lookup"><span data-stu-id="3dda8-108">Description</span></span>|  
|------------|-----------------|  
|`ofsNamespace`|<span data-ttu-id="3dda8-109">Premier offset dans la mémoire tampon de caractères.</span><span class="sxs-lookup"><span data-stu-id="3dda8-109">The first offset into the character buffer.</span></span> <span data-ttu-id="3dda8-110">Cet offset n’est pas suivi de l’espace de noms de l’attribut, mais d’une série de caractères null.</span><span class="sxs-lookup"><span data-stu-id="3dda8-110">This offset is not followed by the attribute's namespace, but by a series of null characters.</span></span> <span data-ttu-id="3dda8-111">Par conséquent, il n’est pas utilisé.</span><span class="sxs-lookup"><span data-stu-id="3dda8-111">Therefore, it is not used.</span></span>|  
|`ofsName`|<span data-ttu-id="3dda8-112">Deuxième offset dans la mémoire tampon de caractères.</span><span class="sxs-lookup"><span data-stu-id="3dda8-112">The second offset into the character buffer.</span></span> <span data-ttu-id="3dda8-113">Cet emplacement marque le début du nom de l’attribut.</span><span class="sxs-lookup"><span data-stu-id="3dda8-113">This location marks the start of the attribute's name.</span></span>|  
|`ofsValue`|<span data-ttu-id="3dda8-114">Troisième offset dans la mémoire tampon de caractères.</span><span class="sxs-lookup"><span data-stu-id="3dda8-114">The third offset into the character buffer.</span></span> <span data-ttu-id="3dda8-115">Cet emplacement marque le début de la valeur de l’attribut.</span><span class="sxs-lookup"><span data-stu-id="3dda8-115">This location marks the start of the attribute's value.</span></span>|  
  
## <a name="sample"></a><span data-ttu-id="3dda8-116">Exemple</span><span class="sxs-lookup"><span data-stu-id="3dda8-116">Sample</span></span>  

 <span data-ttu-id="3dda8-117">L’exemple suivant illustre plusieurs étapes de base, ce qui finit par aboutir à une `IDENTITY_ATTRIBUTE_BLOB` structure remplie :</span><span class="sxs-lookup"><span data-stu-id="3dda8-117">The following example illustrates several basic steps, which eventually result in a populated `IDENTITY_ATTRIBUTE_BLOB` structure:</span></span>  
  
1. <span data-ttu-id="3dda8-118">Obtenez un [IReferenceIdentity](ireferenceidentity-interface.md) pour l’assembly.</span><span class="sxs-lookup"><span data-stu-id="3dda8-118">Obtain an [IReferenceIdentity](ireferenceidentity-interface.md) for the assembly.</span></span>  
  
2. <span data-ttu-id="3dda8-119">Appelez la `IReferenceIdentity::EnumAttributes` méthode et obtenez un [IEnumIDENTITY_ATTRIBUTE](ienumidentity-attribute-interface.md).</span><span class="sxs-lookup"><span data-stu-id="3dda8-119">Call the `IReferenceIdentity::EnumAttributes` method, and obtain an [IEnumIDENTITY_ATTRIBUTE](ienumidentity-attribute-interface.md).</span></span>  
  
3. <span data-ttu-id="3dda8-120">Créez une mémoire tampon de caractères et effectuez un cast de celle-ci en `IDENTITY_ATTRIBUTE_BLOB` structure.</span><span class="sxs-lookup"><span data-stu-id="3dda8-120">Create a character buffer, and cast it as an `IDENTITY_ATTRIBUTE_BLOB` structure.</span></span>  
  
4. <span data-ttu-id="3dda8-121">Appelez la `CurrentIntoBuffer` méthode de l' `IEnumIDENTITY_ATTRIBUTE` interface.</span><span class="sxs-lookup"><span data-stu-id="3dda8-121">Call the `CurrentIntoBuffer` method of the `IEnumIDENTITY_ATTRIBUTE` interface.</span></span> <span data-ttu-id="3dda8-122">Cette méthode copie les attributs `Namespace` , `Name` et `Value` dans la mémoire tampon de caractères.</span><span class="sxs-lookup"><span data-stu-id="3dda8-122">This method copies the attributes `Namespace`, `Name`, and `Value` into the character buffer.</span></span> <span data-ttu-id="3dda8-123">Les trois décalages de ces chaînes deviennent disponibles dans la `IDENTITY_ATTRIBUTE_BLOB` structure.</span><span class="sxs-lookup"><span data-stu-id="3dda8-123">The three offsets to those strings will become available in the `IDENTITY_ATTRIBUTE_BLOB` structure.</span></span>  
  
```cpp  
// EnumAssemblyAttributes.cpp : main project file.  
  
#include "stdafx.h"  
  
#include "fusion.h"  
#include "windows.h"  
#include "stdio.h"  
#include "mscoree.h"  
#include "isolation.h"  
  
typedef HRESULT (__stdcall *PFNGETREF)(LPCWSTR pwzFile, REFIID riid, IUnknown **ppUnk);  
typedef HRESULT (__stdcall *PFNGETAUTH)(IIdentityAuthority **ppIIdentityAuthority);  
  
PFNGETREF                   g_pfnGetAssemblyIdentityFromFile = NULL;  
PFNGETAUTH                  g_pfnGetIdentityAuthority = NULL;  
IUnknown                    *g_pUnk = NULL;  
  
bool Init()  
{  
    HRESULT     hr = S_OK;  
    DWORD       dwSize = 0;  
    bool        bRC = false;  
  
    hr = CorBindToRuntimeEx(NULL, L"wks", 0, CLSID_CorRuntimeHost,  
                           IID_ICorRuntimeHost, (void **)&g_pUnk);  
    if(FAILED(hr)) {  
        printf("Error: Failed to initialize CLR runtime! hr = 0x%0x\n",  
                hr);  
        goto Exit;  
    }  
  
    if (SUCCEEDED(hr)) {  
        hr = GetRealProcAddress("GetAssemblyIdentityFromFile",  
                         (VOID **)&g_pfnGetAssemblyIdentityFromFile);  
    }  
  
    if (SUCCEEDED(hr)) {  
        hr = GetRealProcAddress("GetIdentityAuthority",  
                                (VOID **)&g_pfnGetIdentityAuthority);  
    }  
  
    if (!g_pfnGetAssemblyIdentityFromFile ||
        !g_pfnGetIdentityAuthority)  
    {  
        printf("Error: Cannot get required APIs from fusion.dll!\n");  
        goto Exit;  
    }  
  
    bRC = true;  
  
Exit:  
    return bRC;  
}  
  
void Shutdown()  
{  
    if(g_pUnk) {  
        g_pUnk->Release();  
        g_pUnk = NULL;  
    }  
}  
  
void Usage()  
{  
    printf("EnumAssemblyAttributes: A tool to enumerate the identity
            attributes of a given assembly.\n\n");  
    printf("Usage: EnumAssemblyAttributes AssemblyFilePath\n");  
    printf("\n");  
}  
  
int _cdecl wmain(int argc, LPCWSTR argv[])  
{  
    int     iResult = 1;  
    IUnknown                    *pUnk  = NULL;  
    IReferenceIdentity          *pRef  = NULL;  
    HRESULT                     hr     = S_OK;
    IEnumIDENTITY_ATTRIBUTE     *pEnum = NULL;  
    BYTE                        abData[1024];  
    DWORD                       cbAvailable;  
    DWORD                       cbUsed;  
    IDENTITY_ATTRIBUTE_BLOB     *pBlob;  
  
    if(argc != 2) {  
        Usage();  
        goto Exit;  
    }  
  
    if(!Init()) {  
        printf("Failure initializing EnumIdAttr.\n");  
        goto Exit;  
    }  
  
    hr = g_pfnGetAssemblyIdentityFromFile(argv[1],
                            __uuidof(IReferenceIdentity), &pUnk);  
  
    if (FAILED(hr)) {  
        printf("GetAssemblyIdentityFromFile failed with hr = 0x%x",
                hr);  
        goto Exit;  
    }  
  
    hr = pUnk->QueryInterface(__uuidof(IReferenceIdentity),
                              (void**)&pRef);  
    if (FAILED(hr)) {  
        goto Exit;  
    }  
  
    hr = pRef->EnumAttributes(&pEnum);  
    if (FAILED(hr)) {  
        printf("IReferenceIdentity::EnumAttributes failed with hr =
                0x%x", hr);  
        goto Exit;  
    }  
  
    pBlob = (IDENTITY_ATTRIBUTE_BLOB *)(abData);  
    while (1) {  
        cbAvailable = sizeof(abData);  
        hr = pEnum->CurrentIntoBuffer(cbAvailable, abData, &cbUsed);  
        if (FAILED(hr)) {  
            printf("IEnumIDENTITY_ATTRIBUTE::CurrentIntoBuffer failed
                    with hr = 0x%x", hr);  
            goto Exit;  
        }  
  
        if (! cbUsed) {  
            break;  
        }  
  
        LPWSTR pwzNameSpace = (LPWSTR)(abData + pBlob->ofsNamespace);  
        LPWSTR pwzName      = (LPWSTR)(abData + pBlob->ofsName);  
        LPWSTR pwzValue     = (LPWSTR)(abData + pBlob->ofsValue);  
        printf("%ws: %ws = %ws\n", pwzNameSpace, pwzName, pwzValue);  
  
        hr = pEnum->Skip(1);  
        if (FAILED(hr)) {  
            printf("IEnumIDENTITY_ATTRIBUTE::Skip failed with hr =
                    0x%x", hr);  
            goto Exit;  
        }  
    }  
  
    iResult = 0;  
  
Exit:  
  
    Shutdown();  
  
    if (pUnk) {  
        pUnk->Release();  
    }  
  
    if (pRef) {  
        pRef->Release();  
    }  
  
    if (pEnum) {  
        pEnum->Release();  
    }  
  
    return iResult;  
}  
```  
  
### <a name="to-run-the-sample"></a><span data-ttu-id="3dda8-124">Exécution de l'exemple</span><span class="sxs-lookup"><span data-stu-id="3dda8-124">To run the sample</span></span>  

 <span data-ttu-id="3dda8-125">C : \\> EnumAssemblyAttributes.exe C:\WINDOWS\Microsoft.NET\Framework\v2.0.50727\System.dll</span><span class="sxs-lookup"><span data-stu-id="3dda8-125">C:\\> EnumAssemblyAttributes.exe C:\WINDOWS\Microsoft.NET\Framework\v2.0.50727\System.dll</span></span>  
  
### <a name="sample-output"></a><span data-ttu-id="3dda8-126">Exemple de sortie</span><span class="sxs-lookup"><span data-stu-id="3dda8-126">Sample output</span></span>  

 <span data-ttu-id="3dda8-127">Culture = neutral</span><span class="sxs-lookup"><span data-stu-id="3dda8-127">Culture = neutral</span></span>  
  
 <span data-ttu-id="3dda8-128">Name = System</span><span class="sxs-lookup"><span data-stu-id="3dda8-128">name = System</span></span>  
  
 <span data-ttu-id="3dda8-129">processorArchitecture = MSIL</span><span class="sxs-lookup"><span data-stu-id="3dda8-129">processorArchitecture = MSIL</span></span>  
  
 <span data-ttu-id="3dda8-130">PublicKeyToken = b77a5c561934e089</span><span class="sxs-lookup"><span data-stu-id="3dda8-130">PublicKeyToken = b77a5c561934e089</span></span>  
  
 <span data-ttu-id="3dda8-131">Version = 2.0.0.0</span><span class="sxs-lookup"><span data-stu-id="3dda8-131">Version = 2.0.0.0</span></span>  
  
## <a name="requirements"></a><span data-ttu-id="3dda8-132">Configuration requise</span><span class="sxs-lookup"><span data-stu-id="3dda8-132">Requirements</span></span>  

 <span data-ttu-id="3dda8-133">**Plateformes :** Consultez [Configuration requise](../../get-started/system-requirements.md).</span><span class="sxs-lookup"><span data-stu-id="3dda8-133">**Platforms:** See [System Requirements](../../get-started/system-requirements.md).</span></span>  
  
 <span data-ttu-id="3dda8-134">**En-tête :** Isolation. h</span><span class="sxs-lookup"><span data-stu-id="3dda8-134">**Header:** Isolation.h</span></span>  
  
 <span data-ttu-id="3dda8-135">**Versions de .NET Framework :**[!INCLUDE[net_current_v20plus](../../../../includes/net-current-v20plus-md.md)]</span><span class="sxs-lookup"><span data-stu-id="3dda8-135">**.NET Framework Versions:** [!INCLUDE[net_current_v20plus](../../../../includes/net-current-v20plus-md.md)]</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="3dda8-136">Voir aussi</span><span class="sxs-lookup"><span data-stu-id="3dda8-136">See also</span></span>

- [<span data-ttu-id="3dda8-137">IReferenceIdentity, interface</span><span class="sxs-lookup"><span data-stu-id="3dda8-137">IReferenceIdentity Interface</span></span>](ireferenceidentity-interface.md)
- [<span data-ttu-id="3dda8-138">IEnumIDENTITY_ATTRIBUTE, interface</span><span class="sxs-lookup"><span data-stu-id="3dda8-138">IEnumIDENTITY_ATTRIBUTE Interface</span></span>](ienumidentity-attribute-interface.md)
- [<span data-ttu-id="3dda8-139">IDENTITY_ATTRIBUTE, structure</span><span class="sxs-lookup"><span data-stu-id="3dda8-139">IDENTITY_ATTRIBUTE Structure</span></span>](identity-attribute-structure.md)
- [<span data-ttu-id="3dda8-140">Structures de fusion</span><span class="sxs-lookup"><span data-stu-id="3dda8-140">Fusion Structures</span></span>](fusion-structures.md)
