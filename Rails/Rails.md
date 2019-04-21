## before_actionでのオプション

before_action :confirm_card_info, if: :customer_signed_in?
before_actionでもif文を使用する事ができた。

## deviseのカスタマイズ

- deviseで新規登録後に別のアクションを動かしたい、登録後パスを変更したいと言った場合
コントローラーをカスタマイズする必要があるので**rails g devise:controllers users**コマンドを実行(今回はユーザーモデルをベースにしている)
そうするとapp/controllers/users/confirmations_controller.rbなどのいくつかのファイルができる

次にroutesファイルをいじる

devise_for :users, controllers => {
  :registrations => 'users/registrations' registrationsコントローラーを変更したい場合
}

他にもスコープを使う事ができる
devise_scope :user do
  get 'my_page' => 'users/registrations#my_page'
end

あとはコントローラーにオーバーライドしていけば良い
class Users::RegistrationsController < Devise::RegistrationsController
  before_action :authenticate_user!

  def my_page

  end

  protected

  def after_sign_up_path_for(resource)
     my_page_path
  end
end


