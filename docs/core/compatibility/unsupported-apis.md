---
title: API non prises en charge sur .NET Core
description: Découvrez les API de la .NET Framework qui lèvent toujours une exception sur .NET Core.
ms.date: 12/23/2019
ms.openlocfilehash: f27aeca31226a95dacf100813762eedb56876fbd
ms.sourcegitcommit: 7e2128d4a4c45b4274bea3b8e5760d4694569ca1
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 01/14/2020
ms.locfileid: "75936973"
---
# <a name="apis-that-always-throw-exceptions-on-net-core"></a>API qui lèvent toujours des exceptions sur .NET Core

Les API suivantes lèvent toujours une <xref:System.PlatformNotSupportedException> sur .NET Core sur tout ou partie des plateformes.

Cet article organise les membres d’API affectés par espace de noms.

> [!NOTE]
>
> - Cet article est un travail en cours. Il ne s’agit pas d’une liste complète des API qui lèvent des exceptions sur .NET Core.
> - Cet article n’inclut pas les implémentations d’interface explicites pour la sérialisation binaire qui lèvent sur .NET Core. Pour plus d’informations, consultez [sérialisation binaire dans .net Core](../../standard/serialization/binary-serialization.md#net-core).

## <a name="system"></a>System

| Member | Plateformes qui lèvent |
| - | - |
| <xref:System.AppDomain.CreateDomain%2A?displayProperty=nameWithType> | Toutes les |
| <xref:System.AppDomain.ExecuteAssembly(System.String,System.String[],System.Byte[],System.Configuration.Assemblies.AssemblyHashAlgorithm)?displayProperty=nameWithType> | Toutes les |
| <xref:System.Console.CapsLock?displayProperty=nameWithType> | Linux et macOS |
| <xref:System.Console.NumberLock?displayProperty=nameWithType> | Linux et macOS |
| <xref:System.Delegate.GetObjectData(System.Runtime.Serialization.SerializationInfo,System.Runtime.Serialization.StreamingContext)?displayProperty=nameWithType> | Toutes les |
| <xref:System.Exception.SerializeObjectState?displayProperty=nameWithType> | Toutes les |
| <xref:System.MarshalByRefObject.GetLifetimeService?displayProperty=nameWithType> | Toutes les |
| <xref:System.MarshalByRefObject.InitializeLifetimeService?displayProperty=nameWithType> | Toutes les |
| <xref:System.OperatingSystem.GetObjectData(System.Runtime.Serialization.SerializationInfo,System.Runtime.Serialization.StreamingContext)?displayProperty=nameWithType> | Toutes les |
| <xref:System.Type.ReflectionOnlyGetType(System.String,System.Boolean,System.Boolean)?displayProperty=nameWithType> | Toutes les |

## <a name="systemcodedomcompiler"></a>System.CodeDom.Compiler

| Member | Plateformes qui lèvent |
| - | - |
| <xref:System.CodeDom.Compiler.CodeDomProvider.CompileAssemblyFromDom%2A?displayProperty=nameWithType> | Toutes les |
| <xref:System.CodeDom.Compiler.CodeDomProvider.CompileAssemblyFromFile%2A?displayProperty=nameWithType> | Toutes les |
| <xref:System.CodeDom.Compiler.CodeDomProvider.CompileAssemblyFromSource%2A?displayProperty=nameWithType> | Toutes les |

## <a name="systemcollectionsspecialized"></a>System.Collections.Specialized

| Member | Plateformes qui lèvent |
| - | - |
| <xref:System.Collections.Specialized.NameObjectCollectionBase.%23ctor(System.Runtime.Serialization.SerializationInfo,System.Runtime.Serialization.StreamingContext)?displayProperty=nameWithType> | Toutes les |
| <xref:System.Collections.Specialized.NameObjectCollectionBase.GetObjectData(System.Runtime.Serialization.SerializationInfo,System.Runtime.Serialization.StreamingContext)?displayProperty=nameWithType> | Toutes les |
| <xref:System.Collections.Specialized.NameObjectCollectionBase.OnDeserialization(System.Object)?displayProperty=nameWithType> | Toutes les |

## <a name="systemconfiguration"></a>System.Configuration

| Member | Plateformes qui lèvent |
| - | - |
| <xref:System.Configuration.RsaProtectedConfigurationProvider?displayProperty=nameWithType> (tous les membres) | Toutes les |

## <a name="systemconsole"></a>System.Console

| Member | Plateformes qui lèvent |
| - | - |
| <xref:System.Console.Beep?displayProperty=nameWithType> | Linux et macOS |
| <xref:System.Console.BufferHeight?displayProperty=nameWithType> (définir uniquement) | Linux et macOS |
| <xref:System.Console.BufferWidth?displayProperty=nameWithType> (définir uniquement) | Linux et macOS |
| <xref:System.Console.CursorSize?displayProperty=nameWithType> (définir uniquement) | Linux et macOS |
| <xref:System.Console.CursorVisible?displayProperty=nameWithType> (récupération uniquement) | Linux et macOS |
| <xref:System.Console.MoveBufferArea%2A?displayProperty=nameWithType> | Linux et macOS |
| <xref:System.Console.SetWindowPosition%2A?displayProperty=nameWithType> | Linux et macOS |
| <xref:System.Console.SetWindowSize%2A?displayProperty=nameWithType> | Linux et macOS |
| <xref:System.Console.Title?displayProperty=nameWithType> (récupération uniquement) | Linux et macOS |
| <xref:System.Console.WindowHeight?displayProperty=nameWithType> (définir uniquement) | Linux et macOS |
| <xref:System.Console.WindowLeft?displayProperty=nameWithType> (définir uniquement) | Linux et macOS |
| <xref:System.Console.WindowTop?displayProperty=nameWithType> (définir uniquement) | Linux et macOS |
| <xref:System.Console.WindowWidth?displayProperty=nameWithType> (définir uniquement) | Linux et macOS |

## <a name="systemdatacommon"></a>System.Data.Common

| Member | Plateformes qui lèvent |
| - | - |
| <xref:System.Data.Common.DbDataReader.GetSchemaTable%2A?displayProperty=nameWithType> (lève <xref:System.NotSupportedException>) | Toutes les |

## <a name="systemdiagnosticsprocess"></a>System.Diagnostics.Process

| Member | Plateformes qui lèvent |
| - | - |
| <xref:System.Diagnostics.Process.MaxWorkingSet?displayProperty=nameWithType> (définir uniquement) | Linux |
| <xref:System.Diagnostics.Process.MinWorkingSet?displayProperty=nameWithType> (définir uniquement) | Linux |
| <xref:System.Diagnostics.Process.ProcessorAffinity?displayProperty=nameWithType> | macOS |
| <xref:System.Diagnostics.Process.MainWindowHandle?displayProperty=nameWithType> | Linux et macOS |
| <xref:System.Diagnostics.Process.Start%2A?displayProperty=nameWithType> | Linux et macOS |
| <xref:System.Diagnostics.ProcessStartInfo.UserName?displayProperty=nameWithType> | Linux et macOS |
| <xref:System.Diagnostics.ProcessStartInfo.PasswordInClearText?displayProperty=nameWithType> | Linux et macOS |
| <xref:System.Diagnostics.ProcessStartInfo.Domain?displayProperty=nameWithType> | Linux et macOS |
| <xref:System.Diagnostics.ProcessStartInfo.LoadUserProfile?displayProperty=nameWithType> | Linux et macOS |
| <xref:System.Diagnostics.ProcessThread.BasePriority?displayProperty=nameWithType> (définir uniquement) | Linux et macOS |
| <xref:System.Diagnostics.ProcessThread.BasePriority?displayProperty=nameWithType> (récupération uniquement) | macOS |
| <xref:System.Diagnostics.ProcessThread.ProcessorAffinity?displayProperty=nameWithType> (définir uniquement) | Linux et macOS |

## <a name="systemio"></a>System.IO

| Member | Plateformes qui lèvent |
| - | - |
| <xref:System.IO.FileSystemInfo.%23ctor(System.Runtime.Serialization.SerializationInfo,System.Runtime.Serialization.StreamingContext)?displayProperty=nameWithType> | Toutes les |
| <xref:System.IO.FileSystemInfo.GetObjectData(System.Runtime.Serialization.SerializationInfo,System.Runtime.Serialization.StreamingContext)?displayProperty=nameWithType> | Toutes les |

## <a name="systemiopipes"></a>System.IO.Pipes

| Member | Plateformes qui lèvent |
| - | - |
| <xref:System.IO.Pipes.NamedPipeClientStream.NumberOfServerInstances?displayProperty=nameWithType> | Linux et macOS |
| <xref:System.IO.Pipes.NamedPipeServerStream.GetImpersonationUserName?displayProperty=nameWithType> | Linux et macOS |
| <xref:System.IO.Pipes.PipeStream.InBufferSize?displayProperty=nameWithType> | Linux et macOS |
| <xref:System.IO.Pipes.PipeStream.OutBufferSize?displayProperty=nameWithType> | Linux et macOS |
| <xref:System.IO.Pipes.PipeStream.ReadMode?displayProperty=nameWithType> (définir uniquement) | Linux et macOS |
| <xref:System.IO.Pipes.PipeStream.WaitForPipeDrain?displayProperty=nameWithType> | Linux et macOS |

## <a name="systemmedia"></a>System. Media

| Member | Plateformes qui lèvent |
| - | - |
| <xref:System.Media.SoundPlayer.%23ctor(System.Runtime.Serialization.SerializationInfo,System.Runtime.Serialization.StreamingContext)?displayProperty=nameWithType> | Toutes les |

## <a name="systemnet"></a>System.Net

| Member | Plateformes qui lèvent |
| - | - |
| <xref:System.Net.AuthenticationManager.Authenticate(System.String,System.Net.WebRequest,System.Net.ICredentials)?displayProperty=nameWithType> | Toutes les |
| <xref:System.Net.AuthenticationManager.PreAuthenticate(System.Net.WebRequest,System.Net.ICredentials)?displayProperty=nameWithType> | Toutes les |
| <xref:System.Net.FileWebRequest.%23ctor(System.Runtime.Serialization.SerializationInfo,System.Runtime.Serialization.StreamingContext)?displayProperty=nameWithType> | Toutes les |
| <xref:System.Net.FileWebRequest.GetObjectData(System.Runtime.Serialization.SerializationInfo,System.Runtime.Serialization.StreamingContext)?displayProperty=nameWithType> | Toutes les |
| <xref:System.Net.FileWebResponse.%23ctor(System.Runtime.Serialization.SerializationInfo,System.Runtime.Serialization.StreamingContext)?displayProperty=nameWithType> | Toutes les |
| <xref:System.Net.FileWebResponse.GetObjectData(System.Runtime.Serialization.SerializationInfo,System.Runtime.Serialization.StreamingContext)?displayProperty=nameWithType> | Toutes les |
| <xref:System.Net.HttpWebRequest.%23ctor(System.Runtime.Serialization.SerializationInfo,System.Runtime.Serialization.StreamingContext)?displayProperty=nameWithType> | Toutes les |
| <xref:System.Net.HttpWebRequest.GetObjectData(System.Runtime.Serialization.SerializationInfo,System.Runtime.Serialization.StreamingContext)?displayProperty=nameWithType> | Toutes les |
| <xref:System.Net.HttpWebResponse.%23ctor(System.Runtime.Serialization.SerializationInfo,System.Runtime.Serialization.StreamingContext)?displayProperty=nameWithType> | Toutes les |
| <xref:System.Net.HttpWebResponse.GetObjectData(System.Runtime.Serialization.SerializationInfo,System.Runtime.Serialization.StreamingContext)?displayProperty=nameWithType> | Toutes les |
| <xref:System.Net.WebProxy.%23ctor(System.Runtime.Serialization.SerializationInfo,System.Runtime.Serialization.StreamingContext)?displayProperty=nameWithType> | Toutes les |
| <xref:System.Net.WebProxy.GetDefaultProxy?displayProperty=nameWithType> | Toutes les |
| <xref:System.Net.WebProxy.GetObjectData%2A?displayProperty=nameWithType> | Toutes les |
| <xref:System.Net.WebRequest.%23ctor(System.Runtime.Serialization.SerializationInfo,System.Runtime.Serialization.StreamingContext)?displayProperty=nameWithType> | Toutes les |
| <xref:System.Net.WebRequest.GetObjectData(System.Runtime.Serialization.SerializationInfo,System.Runtime.Serialization.StreamingContext)?displayProperty=nameWithType> | Toutes les |
| <xref:System.Net.WebResponse.%23ctor(System.Runtime.Serialization.SerializationInfo,System.Runtime.Serialization.StreamingContext)?displayProperty=nameWithType> | Toutes les |
| <xref:System.Net.WebResponse.GetObjectData(System.Runtime.Serialization.SerializationInfo,System.Runtime.Serialization.StreamingContext)?displayProperty=nameWithType> | Toutes les |

## <a name="systemnetnetworkinformation"></a>System.Net.NetworkInformation

| Member | Plateformes qui lèvent |
| - | - |
| <xref:System.Net.NetworkInformation.Ping.Send%2A?displayProperty=nameWithType> | Windows (UWP) |

## <a name="systemnetsockets"></a>System.Net.Sockets

| Member | Plateformes qui lèvent |
| - | - |
| <xref:System.Net.Sockets.Socket.DuplicateAndClose(System.Int32)?displayProperty=nameWithType> | Toutes les |

## <a name="systemnetwebsockets"></a>System.Net.WebSockets

| Member | Plateformes qui lèvent |
| - | - |
| <xref:System.Net.WebSockets.WebSocket.RegisterPrefixes?displayProperty=nameWithType> | Toutes les |

## <a name="systemreflection"></a>System.Reflection

| Member | Plateformes qui lèvent |
| - | - |
| <xref:System.Reflection.Assembly.ReflectionOnlyLoad%2A?displayProperty=nameWithType> | Toutes les |
| <xref:System.Reflection.Assembly.ReflectionOnlyLoadFrom(System.String)?displayProperty=nameWithType> | Toutes les |
| <xref:System.Reflection.AssemblyName.GetObjectData(System.Runtime.Serialization.SerializationInfo,System.Runtime.Serialization.StreamingContext)?displayProperty=nameWithType> | Toutes les |
| <xref:System.Reflection.AssemblyName.OnDeserialization(System.Object)?displayProperty=nameWithType> | Toutes les |
| <xref:System.Reflection.StrongNameKeyPair.%23ctor(System.String)?displayProperty=nameWithType> | Toutes les |
| <xref:System.Reflection.StrongNameKeyPair.%23ctor(System.Runtime.Serialization.SerializationInfo,System.Runtime.Serialization.StreamingContext)?displayProperty=nameWithType> | Toutes les |
| <xref:System.Reflection.StrongNameKeyPair.PublicKey?displayProperty=nameWithType> | Toutes les |

## <a name="systemruntimecompilerservices"></a>System.Runtime.CompilerServices

| Member | Plateformes qui lèvent |
| - | - |
| <xref:System.Runtime.CompilerServices.DebugInfoGenerator.CreatePdbGenerator?displayProperty=nameWithType> | Toutes les |

## <a name="systemruntimeinteropservices"></a>System.Runtime.InteropServices

| Member | Plateformes qui lèvent |
| - | - |
| <xref:System.Runtime.InteropServices.Marshal.GetIDispatchForObject(System.Object)?displayProperty=nameWithType> | Toutes les |
| <xref:System.Runtime.InteropServices.RuntimeEnvironment.SystemConfigurationFile?displayProperty=nameWithType> | Toutes les |
| <xref:System.Runtime.InteropServices.RuntimeEnvironment.GetRuntimeInterfaceAsIntPtr(System.Guid,System.Guid)?displayProperty=nameWithType> | Toutes les |
| <xref:System.Runtime.InteropServices.RuntimeEnvironment.GetRuntimeInterfaceAsObject(System.Guid,System.Guid)?displayProperty=nameWithType> | Toutes les |
| <xref:System.Runtime.InteropServices.WindowsRuntime.WindowsRuntimeMarshal.StringToHString(System.String)?displayProperty=nameWithType> | Linux et macOS |
| <xref:System.Runtime.InteropServices.WindowsRuntime.WindowsRuntimeMarshal.PtrToStringHString(System.IntPtr)?displayProperty=nameWithType> | Linux et macOS |
| <xref:System.Runtime.InteropServices.WindowsRuntime.WindowsRuntimeMarshal.FreeHString(System.IntPtr)?displayProperty=nameWithType> | Linux et macOS |

## <a name="systemruntimeserialization"></a>System.Runtime.Serialization

| Member | Plateformes qui lèvent |
| - | - |
| <xref:System.Runtime.Serialization.XsdDataContractExporter.Schemas?displayProperty=nameWithType> | Toutes les |

## <a name="systemsecurity"></a>System.Security

| Member | Plateformes qui lèvent |
| - | - |
| <xref:System.Security.CodeAccessPermission.Deny?displayProperty=nameWithType> | Toutes les |
| <xref:System.Security.CodeAccessPermission.PermitOnly?displayProperty=nameWithType> | Toutes les |
| <xref:System.Security.PermissionSet.ConvertPermissionSet(System.String,System.Byte[],System.String)?displayProperty=nameWithType> | Toutes les |
| <xref:System.Security.PermissionSet.Deny?displayProperty=nameWithType> | Toutes les |
| <xref:System.Security.PermissionSet.PermitOnly?displayProperty=nameWithType> | Toutes les |
| <xref:System.Security.SecurityContext.Capture?displayProperty=nameWithType> | Toutes les |
| <xref:System.Security.SecurityContext.CreateCopy?displayProperty=nameWithType> | Toutes les |
| <xref:System.Security.SecurityContext.Dispose?displayProperty=nameWithType> | Toutes les |
| <xref:System.Security.SecurityContext.IsFlowSuppressed?displayProperty=nameWithType> | Toutes les |
| <xref:System.Security.SecurityContext.IsWindowsIdentityFlowSuppressed?displayProperty=nameWithType> | Toutes les |
| <xref:System.Security.SecurityContext.RestoreFlow?displayProperty=nameWithType> | Toutes les |
| <xref:System.Security.SecurityContext.Run(System.Security.SecurityContext,System.Threading.ContextCallback,System.Object)?displayProperty=nameWithType> | Toutes les |
| <xref:System.Security.SecurityContext.SuppressFlow?displayProperty=nameWithType> | Toutes les |
| <xref:System.Security.SecurityContext.SuppressFlowWindowsIdentity?displayProperty=nameWithType> | Toutes les |

## <a name="systemsecurityclaims"></a>System.Security.Claims

| Member | Plateformes qui lèvent |
| - | - |
| <xref:System.Security.Claims.ClaimsPrincipal.%23ctor?displayProperty=nameWithType> | Toutes les |
| <xref:System.Security.Claims.ClaimsPrincipal.GetObjectData(System.Runtime.Serialization.SerializationInfo,System.Runtime.Serialization.StreamingContext)?displayProperty=nameWithType> | Toutes les |
| <xref:System.Security.Claims.ClaimsIdentity.%23ctor(System.Runtime.Serialization.SerializationInfo)?displayProperty=nameWithType> | Toutes les |
| <xref:System.Security.Claims.ClaimsIdentity.%23ctor(System.Runtime.Serialization.SerializationInfo,System.Runtime.Serialization.StreamingContext)?displayProperty=nameWithType> | Toutes les |
| <xref:System.Security.Claims.ClaimsIdentity.GetObjectData(System.Runtime.Serialization.SerializationInfo,System.Runtime.Serialization.StreamingContext)?displayProperty=nameWithType> | Toutes les |

## <a name="systemsecuritycryptography"></a>System.Security.Cryptography

| Member | Plateformes qui lèvent |
| - | - |
| <xref:System.Security.Cryptography.AsymmetricAlgorithm.Create(System.String)?displayProperty=nameWithType> | Toutes les |
| <xref:System.Security.Cryptography.CspKeyContainerInfo.%23ctor%2A?displayProperty=nameWithType> | Linux et macOS |
| <xref:System.Security.Cryptography.CspKeyContainerInfo.Accessible?displayProperty=nameWithType> | Linux et macOS |
| <xref:System.Security.Cryptography.CspKeyContainerInfo.Exportable?displayProperty=nameWithType> | Linux et macOS |
| <xref:System.Security.Cryptography.CspKeyContainerInfo.HardwareDevice?displayProperty=nameWithType> | Linux et macOS |
| <xref:System.Security.Cryptography.CspKeyContainerInfo.KeyContainerName?displayProperty=nameWithType> | Linux et macOS |
| <xref:System.Security.Cryptography.CspKeyContainerInfo.KeyNumber?displayProperty=nameWithType> | Linux et macOS |
| <xref:System.Security.Cryptography.CspKeyContainerInfo.MachineKeyStore?displayProperty=nameWithType> | Linux et macOS |
| <xref:System.Security.Cryptography.CspKeyContainerInfo.Protected?displayProperty=nameWithType> | Linux et macOS |
| <xref:System.Security.Cryptography.CspKeyContainerInfo.ProviderName?displayProperty=nameWithType> | Linux et macOS |
| <xref:System.Security.Cryptography.CspKeyContainerInfo.ProviderType?displayProperty=nameWithType> | Linux et macOS |
| <xref:System.Security.Cryptography.CspKeyContainerInfo.RandomlyGenerated?displayProperty=nameWithType> | Linux et macOS |
| <xref:System.Security.Cryptography.CspKeyContainerInfo.Removable?displayProperty=nameWithType> | Linux et macOS |
| <xref:System.Security.Cryptography.CspKeyContainerInfo.UniqueKeyContainerName?displayProperty=nameWithType> | Linux et macOS |
| <xref:System.Security.Cryptography.HashAlgorithm.Create?displayProperty=nameWithType> | Toutes les |
| <xref:System.Security.Cryptography.HashAlgorithm.Create(System.String)?displayProperty=nameWithType> | Toutes les |
| <xref:System.Security.Cryptography.HMAC.Create?displayProperty=nameWithType> | Toutes les |
| <xref:System.Security.Cryptography.HMAC.Create(System.String)?displayProperty=nameWithType> | Toutes les |
| <xref:System.Security.Cryptography.HMAC.HashCore%2A?displayProperty=nameWithType> | Toutes les |
| <xref:System.Security.Cryptography.HMAC.HashFinal%2A?displayProperty=nameWithType> | Toutes les |
| <xref:System.Security.Cryptography.HMAC.Initialize%2A?displayProperty=nameWithType> | Toutes les |
| <xref:System.Security.Cryptography.KeyedHashAlgorithm.Create?displayProperty=nameWithType> | Toutes les |
| <xref:System.Security.Cryptography.KeyedHashAlgorithm.Create(System.String)?displayProperty=nameWithType> | Toutes les |
| <xref:System.Security.Cryptography.ProtectedData.Protect%2A?displayProperty=nameWithType> | Linux et macOS |
| <xref:System.Security.Cryptography.ProtectedData.Unprotect%2A?displayProperty=nameWithType> | Linux et macOS |
| <xref:System.Security.Cryptography.RSA.FromXmlString%2A?displayProperty=nameWithType> | Toutes les |
| <xref:System.Security.Cryptography.RSA.ToXmlString%2A?displayProperty=nameWithType> | Toutes les |
| <xref:System.Security.Cryptography.SymmetricAlgorithm.Create?displayProperty=nameWithType> | Toutes les |
| <xref:System.Security.Cryptography.SymmetricAlgorithm.Create(System.String)?displayProperty=nameWithType> | Toutes les |

## <a name="systemsecuritycryptographypkcs"></a>System.Security.Cryptography.Pkcs

| Member | Plateformes qui lèvent |
| - | - |
| <xref:System.Security.Cryptography.Pkcs.CmsSigner.%23ctor(System.Security.Cryptography.CspParameters)?displayProperty=nameWithType> | Toutes les |
| <xref:System.Security.Cryptography.Pkcs.SignedCms.ComputeSignature(System.Security.Cryptography.Pkcs.CmsSigner,System.Boolean)?displayProperty=nameWithType> | Toutes les |
| <xref:System.Security.Cryptography.Pkcs.SignerInfo.ComputeCounterSignature?displayProperty=nameWithType> | Toutes les |

## <a name="systemsecuritycryptographyx509certificates"></a>System.Security.Cryptography.X509Certificates

| Member | Plateformes qui lèvent |
| - | - |
| <xref:System.Security.Cryptography.X509Certificates.X509Certificate.%23ctor(System.Runtime.Serialization.SerializationInfo,System.Runtime.Serialization.StreamingContext)?displayProperty=nameWithType> | Toutes les |
| <xref:System.Security.Cryptography.X509Certificates.X509Certificate.Import%2A?displayProperty=nameWithType> | Toutes les |
| <xref:System.Security.Cryptography.X509Certificates.X509Certificate2.%23ctor(System.Runtime.Serialization.SerializationInfo,System.Runtime.Serialization.StreamingContext)?displayProperty=nameWithType> | Toutes les |
| <xref:System.Security.Cryptography.X509Certificates.X509Certificate2.PrivateKey?displayProperty=nameWithType> (définir uniquement) | Toutes les |

## <a name="systemsecurityauthenticationextendedprotection"></a>System.Security.Authentication.ExtendedProtection

| Member | Plateformes qui lèvent |
| - | - |
| <xref:System.Security.Authentication.ExtendedProtection.ExtendedProtectionPolicy.%23ctor(System.Runtime.Serialization.SerializationInfo,System.Runtime.Serialization.StreamingContext)?displayProperty=nameWithType> | Toutes les |

## <a name="systemsecuritypolicy"></a>System. Security. Policy

| Member | Plateformes qui lèvent |
| - | - |
| <xref:System.Security.Policy.Hash.GetObjectData(System.Runtime.Serialization.SerializationInfo,System.Runtime.Serialization.StreamingContext)?displayProperty=nameWithType> | Toutes les |

## <a name="systemserviceprocessservicecontroller"></a>System.ServiceProcess.ServiceController

| Member | Plateformes qui lèvent |
| - | - |
| <xref:System.ServiceProcess.TimeoutException.%23ctor(System.Runtime.Serialization.SerializationInfo,System.Runtime.Serialization.StreamingContext)?displayProperty=nameWithType> | Toutes les |

## <a name="systemtextregularexpressions"></a>System.Text.RegularExpressions

| Member | Plateformes qui lèvent |
| - | - |
| <xref:System.Text.RegularExpressions.Regex.CompileToAssembly%2A?displayProperty=nameWithType> | Toutes les |

## <a name="systemthreading"></a>System.Threading

| Member | Plateformes qui lèvent |
| - | - |
| <xref:System.Threading.CompressedStack.GetObjectData(System.Runtime.Serialization.SerializationInfo,System.Runtime.Serialization.StreamingContext)?displayProperty=nameWithType> | Toutes les |
| <xref:System.Threading.ExecutionContext.GetObjectData(System.Runtime.Serialization.SerializationInfo,System.Runtime.Serialization.StreamingContext)?displayProperty=nameWithType> | Toutes les |
| <xref:System.Threading.Thread.Abort%2A?displayProperty=nameWithType> | Toutes les |
| <xref:System.Threading.Thread.ResetAbort?displayProperty=nameWithType> | Toutes les |
| <xref:System.Threading.Thread.Resume?displayProperty=nameWithType> | Toutes les |
| <xref:System.Threading.Thread.Suspend?displayProperty=nameWithType> | Toutes les |

## <a name="systemxml"></a>System.Xml

| Member | Plateformes qui lèvent |
| - | - |
| <xref:System.Xml.XmlDictionaryReader.CreateMtomReader(System.Byte[],System.Int32,System.Int32,System.Text.Encoding[],System.String,System.Xml.XmlDictionaryReaderQuotas,System.Int32,System.Xml.OnXmlDictionaryReaderClose)?displayProperty=nameWithType> | Toutes les |
| <xref:System.Xml.XmlDictionaryReader.CreateMtomReader(System.IO.Stream,System.Text.Encoding[],System.String,System.Xml.XmlDictionaryReaderQuotas,System.Int32,System.Xml.OnXmlDictionaryReaderClose)?displayProperty=nameWithType> | Toutes les |
| <xref:System.Xml.XmlDictionaryWriter.CreateMtomWriter(System.IO.Stream,System.Text.Encoding,System.Int32,System.String,System.String,System.String,System.Boolean,System.Boolean)?displayProperty=nameWithType> | Toutes les |

## <a name="see-also"></a>Voir aussi

- [Dernières modifications pour la migration de .NET Framework vers .NET Core](../compatibility/fx-core.md)
- [Sérialisation binaire dans .NET Core](../../standard/serialization/binary-serialization.md#net-core)
- [Analyseur de portabilité .NET](../../standard/analyzers/portability-analyzer.md)
