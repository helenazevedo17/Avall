# Exemplo de Navegação Completa com Formulário e AsyncStorage

Este projeto demonstra como implementar uma navegação completa entre telas utilizando o Expo Router, incluindo um formulário que salva e recupera dados usando o `AsyncStorage`.

## Funcionalidades

- Navegação entre múltiplas telas com Expo Router.
- Formulário para entrada de dados do usuário.
- Salvamento e recuperação dos dados do formulário usando `@react-native-async-storage/async-storage`.
- Suporte a temas claro e escuro.

## Estrutura de Pastas

```
app/
  _layout.tsx           # Layout principal com navegação
  form.tsx              # Tela do formulário
  success.tsx           # Tela de sucesso após envio
components/
  Form.tsx              # Componente reutilizável de formulário
```

## Instalação

1. Instale as dependências:
   ```bash
   npm install
   npm install @react-native-async-storage/async-storage
   ```

2. Inicie o projeto:
   ```bash
   npx expo start
   ```

## Exemplo de Uso

### Navegação

A navegação é configurada em `app/_layout.tsx` usando o `Stack` do Expo Router, permitindo transições entre as telas do formulário e de sucesso.

### Formulário com AsyncStorage

O formulário (`app/form.tsx`) utiliza o `AsyncStorage` para salvar os dados localmente:

```tsx
import AsyncStorage from '@react-native-async-storage/async-storage';

async function salvarDadosFormulario(dados) {
  try {
    await AsyncStorage.setItem('@formulario', JSON.stringify(dados));
  } catch (e) {
    // Tratar erro
  }
}

async function carregarDadosFormulario() {
  try {
    const json = await AsyncStorage.getItem('@formulario');
    return json != null ? JSON.parse(json) : null;
  } catch (e) {
    // Tratar erro
  }
}
```

### Fluxo

1. O usuário preenche o formulário e envia.
2. Os dados são salvos no `AsyncStorage`.
3. O app navega para a tela de sucesso.
4. Ao retornar, os dados podem ser recuperados e exibidos.

## Referências

- [Expo Router](https://docs.expo.dev/router/introduction/)
- [AsyncStorage](https://react-native-async-storage.github.io/async-storage/docs/usage/)
- [React Navigation](https://reactnavigation.org/docs/getting-started/)

---
Adapte os arquivos conforme necessário para o seu fluxo de navegação e campos do formulário.
