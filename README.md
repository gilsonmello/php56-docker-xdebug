# Configurando o PHP 5.6 com Linux, Docker e Xdebug no VScode

- [ ] Instale a extensão Xdebug(https://marketplace.visualstudio.com/items?itemName=xdebug.php-debug)
- [ ] No menu "Run and Debug", clique em "create a launch.json file" e escolha a opção PHP
- [ ] Abra o arquivo launch.json e substitua com a configuração abaixo
```json
{
  "version": "0.2.0",
  "configurations": [
    {
      "name": "Listen for Xdebug",
      "type": "php",
      "request": "launch",
      "port": 9000,
      "pathMappings": {
        "/var/www/app": "${workspaceFolder}"
      },
      "ignore": [
        "**/vendor/**/*.php"
      ]
    }
  ]
}
```
- [ ] No menu "Run and Debug", Selecione a opção "Listen for Xdebug" e clique no botão "Play" ou "Start Debugging (F5)"
- [ ] Abra o terminal e suba os containers php e nginx com o comando
```bash
docker compose up -d
```
- [ ] Abra o arquivo index.php e coloque breakpoint em alguma linha de execução
- [ ] Por último, em um browser, rode o link http://localhost:8080 e o breakpoint deve travar a execução do fluxo