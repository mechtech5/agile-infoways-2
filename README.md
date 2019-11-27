git clone
composer install
npm install && npm run dev
cp .env.example .env
php artisan migrate
php artisan passport:install

Login and Register - JWT Token

#Components
Login
Register
Articles

#Controllers
ArticleController
UserController