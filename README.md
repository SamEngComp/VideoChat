# SocketChat - Chat iOS com NWConnection

![Swift](https://img.shields.io/badge/Swift-5.9-orange.svg)
![Plataforma](https://img.shields.io/badge/plataforma-iOS_17+-blue.svg)

Aplicativo de chat em tempo real usando o framework `Network` da Apple para comunicação via sockets entre dispositivos na mesma rede.

## 📱 Funcionalidades
- **Chat P2P**: Comunicação via TCP
- **Multi-dispositivos**: Arquitetura host/cliente
- **Broadcast**: Envie mensagens para todos conectados
- **Auto-detecção**: Identificação automática do IP local

## 🛠️ Requisitos
- Xcode 15+
- Dispositivos iOS 17+ (ou simuladores)
- Dispositivos devem estar na mesma rede Wi-Fi

## 🚀 Como Testar

### Entre o Mac e o iPhones (Recomendado)
1. **Dispositivo Host (Mac)**:
   - Abra o app → Toque em "Create Room"
   - Anote o IP exibido (ex: `192.168.1.100`)

2. **Dispositivo Cliente (iPhone)**:
   - Cole o IP do host no campo "IP de Conexão"
   - Toque em "Join Room"

3. **Comece a conversar**:
   - As mensagens aparecerão em tempo real nos dois dispositivos

## 🔍 Solução de Problemas
- **Conexão falha?** Verifique:
  - Ambos dispositivos estão no mesmo Wi-Fi
  - Firewall desativado (no Mac: Preferências do Sistema > Segurança)
  - Porta 8080 livre (no Terminal: `nc -zv IP_DO_HOST 8080`)

- **IP incorreto?** No dispositivo host:
  ```swift
  // No código:
  print("IP Local: \(getLocalIPAddress() ?? "Não encontrado")")
  ```

## 📸 Telas
| Tela Inicial | Tela Host | Tela Cliente |
|-----------|-------------| -------------|
| ![IMG_7222](https://github.com/user-attachments/assets/65d4bf1b-321b-4be9-af39-f106069aa75a) | ![IMG_7224](https://github.com/user-attachments/assets/ca6bd3f9-71d8-4703-8deb-3ff0c3ea4481) | ![IMG_7223](https://github.com/user-attachments/assets/3ff2221e-6d75-4b8d-8c0b-e9b4e62c4900)|


## 🧠 Detalhes Técnicos
```swift
// Estrutura principal:
- NWListener (para o host)
- NWConnection (para clientes)
- Serialização JSON das mensagens
- @Observable para atualizações na UI
```

## 📝 Notas para Professores
Para testar corretamente:
1. Abra `SocketChat.xcodeproj` no Xcode 15+
2. Conecte dois iPhones via USB ou use:
   - 1 iPhone físico + 1 simulador
3. Monitore os logs no Xcode (⌘ + ⇧ + C) para ver erros
