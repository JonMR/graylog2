# graylog2 cookbook

Cookbook for java/play based graylog2 v0.20 and up, both server and web interface.

# Requirements

Tested the cookbook with virtualbox 4.3 and vagrant 1.4.3

# Usage

Run default recipe to install server with web interface.

# Attributes

Graylog2 server

* default[:graylog2][:server_version] = '0.20.0'
* default[:graylog2][:server_home] = '/opt/graylog2-server'
* default[:graylog2][:server_user] = 'graylog2'
* default[:graylog2][:server_group] = 'graylog2'
* default[:graylog2][:server_package] = "https://github.com/Graylog2/graylog2-server/releases/download/#{node[:graylog2][:server_version]}/graylog2-server-#{node[:graylog2][:server_version]}.tgz"
* default[:graylog2][:server_password_secret] = "eepahkohd9ieliecaejienahkamohpucaengoisaipeileeghohquohsaijoorohpagheiboodahkeelahraxahmaejoujahifeb7imeyoingaeyiequucuugholaayaicheedaemunguvahgieghihahnailakahmeebeighahtieshahquiegoogaecailgah0aijahvaivaefeekopheilaeyothixepoxaiwieyohyeghiefiungomiesookahtaitootaitaipielahaighoomereehahl9upiixohxoorusiengoquooviuthekephidalaesoopeephiuquahhaingooroofenaediexoakohtheiceiseecahvaeeshob7poonooquohmaileniejateivaipahsaijahveleingooquushooxiiphoohufi" # You MUST set a secret to secure/pepper the stored user passwords here. Use at least 64 characters. Generate one by using for example: pwgen -s 96
* default[:graylog2][:server_root_password_sha2] = "8c6976e5b5410415bde908bd4dee15dfb167a9c873fc4bb8a81f6f2ab448a918" # admin Create one by using for example: echo -n admin | shasum -a 256
* default[:graylog2][:server_rest_listen_uri] = "http://127.0.0.1:12900/"
* default[:graylog2][:server_shards] = 1
* default[:graylog2][:server_replicas] = 0
* default[:graylog2][:server_max_indexes] = 10
* default[:graylog2][:server_max_docs_per_index] = 20000000
* default[:graylog2][:server_mongodb_auth] = false
* default[:graylog2][:server_mongodb_username] = "graylog2"
* default[:graylog2][:server_mongodb_password] = "graylog2"

Graylog2 web interface

* default[:graylog2][:server_version] = '0.20.0'
* default[:graylog2][:server_home] = '/opt/graylog2-server'
* default[:graylog2][:server_user] = 'graylog2'
* default[:graylog2][:server_group] = 'graylog2'
* default[:graylog2][:server_package] = "https://github.com/Graylog2/graylog2-server/releases/download/#{node[:graylog2][:server_version]}/graylog2-server-#{node[:graylog2][:server_version]}.tgz"
* default[:graylog2][:server_password_secret] = "eepahkohd9ieliecaejienahkamohpucaengoisaipeileeghohquohsaijoorohpagheiboodahkeelahraxahmaejoujahifeb7imeyoingaeyiequucuugholaayaicheedaemunguvahgieghihahnailakahmeebeighahtieshahquiegoogaecailgah0aijahvaivaefeekopheilaeyothixepoxaiwieyohyeghiefiungomiesookahtaitootaitaipielahaighoomereehahl9upiixohxoorusiengoquooviuthekephidalaesoopeephiuquahhaingooroofenaediexoakohtheiceiseecahvaeeshob7poonooquohmaileniejateivaipahsaijahveleingooquushooxiiphoohufi" # You MUST set a secret to secure/pepper the stored user passwords here. Use at least 64 characters. Generate one by using for example: pwgen -s 96
* default[:graylog2][:server_root_password_sha2] = "8c6976e5b5410415bde908bd4dee15dfb167a9c873fc4bb8a81f6f2ab448a918" # admin Create one by using for example: echo -n admin | shasum -a 256
* default[:graylog2][:server_rest_listen_uri] = "http://127.0.0.1:12900/"
* default[:graylog2][:server_shards] = 1
* default[:graylog2][:server_replicas] = 0
* default[:graylog2][:server_max_indexes] = 10
* default[:graylog2][:server_max_docs_per_index] = 20000000
* default[:graylog2][:server_mongodb_auth] = false
* default[:graylog2][:server_mongodb_username] = "graylog2"
* default[:graylog2][:server_mongodb_password] = "graylog2"

Graylog2 nginx

* default[:graylog2][:nginx_port] = 80
* default[:graylog2][:nginx_location] = "/"
* override[:nginx][:default_site_enabled] = false

JDK override

* override[:java][:install_flavor] = "openjdk"
* override[:java][:jdk_version] = "7"
* override[:java][:openjdk_packages] = ["openjdk-7-jdk", "openjdk-7-jre-headless"]

ElasticSearch override

* override[:elasticsearch][:cluster][:name] = "graylog2"
* override[:elasticsearch][:bootstrap][:mlockall] = "graylog2"
* override[:elasticsearch][:allocated_memory] = "512m"
* override[:elasticsearch][:plugins] = {"mobz/elasticsearch-head" => ""}

# Recipes

* recipe "graylog2::default", "Installs and configures a graylog2 server"
* recipe "graylog2::server", "Installs and configures a graylog2 server"
* recipe "graylog2::web-interface", "Installs and configures a graylog2 web interface"
* recipe "graylog2::nginx", "Installs and configures a nginx as reverse proxy for the graylog2 web interface"

# Author

Author:: Stephan Oudmaijer (soudmaijer@gmail.com)
