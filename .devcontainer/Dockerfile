FROM debian:latest

# Definir variáveis para o usuário e senha
ENV USERNAME=leonel
ENV PASSWORD=1234
ENV LANG=pt_BR.UTF-8
ENV LANGUAGE=pt_BR:pt
ENV LC_ALL=pt_BR.UTF-8

# Atualizar pacotes, instalar sudo e configurar o idioma
RUN apt update && apt install -y rsyslog systemd-cron systemd sudo locales \
    && rm -f /usr/local/bin/systemctl \
    && echo "pt_BR.UTF-8 UTF-8" > /etc/locale.gen && \
    locale-gen && \
    update-locale LANG=pt_BR.UTF-8 && \
    apt-get clean && rm -rf /var/lib/apt/lists/*
    
# Criar usuário e definir senha
RUN useradd -m -s /bin/bash $USERNAME && \
    echo "$USERNAME:$PASSWORD" | chpasswd && \
    usermod -aG sudo $USERNAME
    
CMD ["/lib/systemd/systemd", "--system", "--unit=basic.target"]
USER leonel
