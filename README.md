# Template OpenGL CMake

Este projeto é um template básico para iniciar projetos OpenGL utilizando CMake. Ele fornece uma estrutura inicial para facilitar o desenvolvimento e a organização do código.

## Funcionalidades

- Suporte a CMake para fácil compilação multiplataforma
- Exemplo básico com OpenGL

## Como usar

1. Clone este repositório:
    ```bash
    git clone https://github.com/psnogueira/template-opengl-cmake.git
    ```
2. Compile o projeto:
    ```bash
    cd template-opengl-cmake
    mkdir build && cd build
    cmake ..
    cmake --build .
    ```
3. Execute o arquivo .exe gerado na pasta `build`.

## Dependências

- CMake >= v3.16
- OpenGL v3.3
- GLFW v3.4
- GLAD

As dependências podem ser gerenciadas via CMake ou adicionadas manualmente conforme necessário.

## Estrutura do Projeto

```
template-opengl-cmake/
├── build/
├── include/
│   ├── glad/
│   └── glfw-3.4/
├── src/
│   └── main.cpp
├── CMakeLists.txt
├── README.md
```

- `build/`: Diretório gerado para arquivos de build.
- `include/`: Arquivos de cabeçalho e dependências.
- `src/`: Código-fonte principal do projeto.
- `CMakeLists.txt`: Arquivo de configuração do CMake.
- `README.md`: Documentação do projeto.

## Licença

Este projeto está licenciado sob a licença [MIT](LICENSE.md).