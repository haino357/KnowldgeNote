# CI/CDとは
Continuous Integration／Continuous Delivery
継続的インティグレーション／継続的デリバリー

CI/CDは1つの技術を指すものでなく、ソフトウェアの変更を常にテストして自動で本番環境にリリース可能な状態にしておく、ソフトウェア開発の手法を意味します。CI/CDを取り入れると、バグを素早く発見したり、変更を自動でリリースしたりできるようになります。

CI/CDには大きく分けてオンプレミス型とクラウド型があり、オンプレミス型としてはJenkins、クラウド型としてはTravis CIやCircleCIなどが有名です。オンプレミス型は一般的に拡張性が高い一方、自分たちで構築・運用する管理コストが発生します。クラウド型は拡張性が低いですが、サーバーなどを自前で用意する必要がなく、すぐに使い始めることができるのが大きな魅力です。

オンプレミス型
- [Jenkins](https://jenkins.io/)
- [Concourse CI](https://concourse-ci.org/)
- [Drone(クラウド版もあり）](http://try.drone.io/)

クラウド型
- [Travis CI](https://travis-ci.org/)
- [CircleCI](https://circleci.jp/)
- [Wercker](http://www.wercker.com/platform)
- [Codeship](https://codeship.com/)
- [AWS CodeBuild](https://aws.amazon.com/jp/codebuild/)
- [GCP Cloud Build](https://cloud.google.com/cloud-build/?hl=ja)