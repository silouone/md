# Commande a retenir/tuto/methode 
## docker
    docker-compose up -d
    docker ps
    dc ps
    dc kill
    docker kill
    docker kill $(docker ps -a) a verifier

## zsh raccourci
 code ./
 gss git status
 gco git checkout

## vscode raccourci
    creation markdown .md + visualisation
    personaliser raccourci 
    ctrl shift + p
    ctrl + R : lister repo

## github 
    git rebase -i <numero commit precedant celui sur lequel on veux squash>
    git cherry-pick <numero commit a cherry pick>

## publish sur canari
    voir la methode de Chris

## mettre en prod
    npm run publish@latest

## tuto et doc a lire 
    https://lodash.com/

## repo ( pb node module)
    npx lerna clean


## lecture usb boot ubuntu

gksu gparted 

## exemple render as props 

import React from 'react';
import PropTypes from 'prop-types';
import SlidesPlayer from './slides/slides-player';
import Header from './player-header';
import style from './style.css';
import IsIE from '../../../hoc/isie';

const SlidePlayer = props => {
  const {header, player} = props;
  const backgroundImage = player.backgroundUrl ? `url(${player.backgroundUrl})` : null;
  // const isIE11 = !!window.MSInputMethodContext && !!document.documentMode;
  const customMarginIE = {marginTop: 0};
  return (
    <div data-name="slidePlayer" className={style.wrapper}>
      <Header {...header} />
      <IsIE >
        {
          isIE => ( 
            style={customMarginIE11}
          <div className={style.wrapperImg}>
            <div className={style.img} style={{backgroundImage}} />
          </div>
          )          
        }       
      </IsIE>
      <div className={style.playerWrapper}>
        <SlidesPlayer {...player} />
      </div>
    </div>
  );
};

SlidePlayer.propTypes = {
  header: PropTypes.shape(Header.propTypes),
  player: PropTypes.shape(SlidesPlayer.propTypes),
  IsIE: PropTypes.bool
};

export default SlidePlayer;
class IsIE extends React.Component {
  state = {isIE: false};

  componentDidMount() {
    const isIE = detectIe();
    this.setState(() => ({
      isIE
    }));
  }

  render() {
    const {children} = this.props;
    const {isIE} = this.state;

    return children(isIE);
  }
}

export default IsIE;

## clean fichier non tracké par github

git clean -xdf