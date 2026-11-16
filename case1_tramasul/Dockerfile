# Usa o Nginx leve baseado em Alpine Linux
FROM nginx:alpine

# Remove a página padrão do Nginx
RUN rm -rf /usr/share/nginx/html/*

# Copia o seu index.html para o diretório público do Nginx
COPY index.html /usr/share/nginx/html/index.html

# Expõe a porta 80 (padrão HTTP para EC2 / ALB)
EXPOSE 80

# Substitui "web-srv-01" pelo valor da variável INSTANCE_LABEL (ou pelo ID/Hostname do container) ao iniciar
CMD ["/bin/sh", "-c", "sed -i \"s/web-srv-01/${INSTANCE_LABEL:-$(hostname)}/g\" /usr/share/nginx/html/index.html && exec nginx -g 'daemon off;'"]