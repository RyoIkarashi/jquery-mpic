#jQuery.mpic

�X�N���[���ɍ��킹�ē�����Đ�����R���e���c����������jQuery�v���O�C���ł��B����Ƃ͂����Ă��d�g�݂͐Î~������Ԃɐ؂�ւ��p���p������ł��B

##Demo

http://nbnote.github.io/jquery-mpic/

##�g����

###�Î~���p�ӂ���

�����1�t���[�����Ƃ̐Î~��ŗp�ӂ��܂��B�X�N���[�����̕\���Ɏg���������y�ʂȉ摜�ƁA�X�N���[����~���ɕ\������傫���Y��ȉ摜�̓��ޗp�ӂ��Ă����܂�(�O�҂݂̂ł��v���O�C���͎g�p�\)�B�܂��A�t�@�C�����͂ǂ����1����n�܂�ʔԂ�t���Ă����Ă��������B

###HTML

�R���e�i�ƂȂ��v�f���L�q���Ă����܂��B

    <div id="screen"></div>

###CSS

�X�N���[�����Ă���ʏ�̈ʒu���ς��Ȃ��悤�Œ肵�Ă����܂��B

    #screen {
      position: fixed;
    }

###JavaScript

jQuery��jQuery.mpic��ǂݍ��܂��Ă����A�^�[�Q�b�g�v�f�Ƀv���O�C����K�{�p�����[�^��ݒ肵�ČĂяo���܂��B���L�̋L�q�ɂ���p�����[�^�͂��ׂĕK�{�ł��Bimg�Ƃ����t�H���_�̒���lq_1.jpg�`lq_100.jpg��100���̉摜�Őݒ肷��ꍇ�̗�ƂȂ�܂��B
�Ăяo���Ɠ����ɂ��ׂĂ̏��摜�̓ǂݍ��݂��J�n�A������ɕ\�����܂��B

    // DOM Ready
    jQuery(function($){
      	$( '#screen' ).mpic({
      	  numFrames: 100, // �K�{�B���t���[���������
      	  lq: 'img/lq_{{index}}.jpg' // �K�{�B���摜�̃p�X���w��B�u{{index}}�v�̕�����ʔԂƂ��ď������܂�
      	});
    });

###��ʒu�ɂ���

�摜�̓E�B���h�E�̃T�C�Y�ɍ��킹�Č��Ԃ��ł��Ȃ��悤���T�C�Y����܂����A���̍ہA�ǂ̈ʒu����ɂ��邩��1�`9�̐����Ŏw�肷�邱�Ƃ��ł��܂��B
1=�����A2=���A3=�E���A4=���A5=�����A6=�E�A7=����A8=��A9=�E��

    // DOM Ready
    jQuery(function($){
      	$( '#screen' ).mpic({
      	  numFrames: 100,
      	  lq: 'img/lq_{{index}}.jpg',
      	  align: 1 // �f�t�H���g��5
      	});
    });

###��摜�ɂ���

�p�X��ݒ肵�Ă����΃X�N���[����~��A�����I�ɑΉ������摜��ǂݍ��݁E�\�����܂�(�v�����[�h�͂��܂���)�B

    // DOM Ready
    jQuery(function($){
      	$( '#screen' ).mpic({
      	  numFrames: 100,
      	  lq: 'img/lq_{{index}}.jpg',
      	  align: 1,
      	  hq: 'img/hq_{{index}}.jpg' // ���摜�Ɠ����悤�ɉ摜�̃p�X���w��
      	});
    });

###�C�x���g�ɂ���

�������̃C�x���g�ɑ΂��ăn���h����ݒ�ł��A�܂������œn�����I�u�W�F�N�g����F�X�ȃf�[�^���Q�Ƃł��܂�(���l�C�e�B�u��Event�Ƃ͊֌W�Ȃ�������Object�ł�)�Bfunction����this�̎Q�Ƃ̓v���O�C���Ăяo�����̗v�f(HTMLElement)�ł��B

    // DOM Ready
    jQuery(function($){
      $( '#screen' ).mpic({
        numFrames: 100,
        lq: 'img/lq_{{index}}.jpg',
        align: 1,
        hq: 'img/hq_{{index}}.jpg',
        
        // ���摜�̓ǂݍ��݂��ꖇ�������邲�ƂɌĂяo�����
        onLoadProgress: function( e ) {
          // �C�x���g�^�C�v
          console.log( e.type ); // �o��: 'loadprogress'
          // �ǂݍ��݂̐i��(�S����)
          console.log( e.percent ); // �o��: 10
          
          // �ǂݍ��݂����������摜(Image�I�u�W�F�N�g)
          console.log( e.data.img ); // �o��: Image
          // �ǂݍ��݂������������摜�̃p�X
          console.log( e.data.src ); // �o��: 'img/lq_10.jpg'
          // �ǂݍ��݂������������摜�ɑΉ������摜�̃p�X(�ݒ肳��Ă���ꍇ)
          console.log( e.data.hq ); // �o��: 'img/hq_10.jpg'
        },
        
        // ���ׂĂ̏��摜�̓ǂݍ��݂������������ɌĂяo�����
        onLoadComplete: function( e ) {
          // �C�x���g�^�C�v
          console.log( e.type ); // �o��: 'loadcomplete'
          
          // �ǂݍ��݊��������f�[�^�ꎮ
          console.log( e.data ); // �o��: [ { img: Image, src: 'img/lq_1.jpg', hq: 'img/lq_1.jpg' }, ... ]
          console.log( e.data[0].img ); // �o��: Image
          console.log( e.data[0].src ); // �o��: 'img/lq_1.jpg'
          console.log( e.data[0].hq ); // �o��: 'img/hq_1.jpg'
        },
        
        // �X�N���[���ɂ���ĉ摜���؂�ւ�����x�ɌĂяo�����
        onUpdate: function( e ) {
          // �C�x���g�^�C�v
          console.log( e.type ); // �o��: 'update'
          // ���܉����ڂ̉摜��
          console.log( e.frameNumber ); // �o��: 10
          
          // �\������Ă���摜(Image�I�u�W�F�N�g)
          console.log( e.data.img ); // �o��: Image
          // �\������Ă��鏬�摜�̃p�X
          console.log( e.data.src ); // �o��: 'img/lq_10.jpg'
          // �\������Ă��鏬�摜�ɑΉ������摜�̃p�X(�ݒ肳��Ă���ꍇ)
          console.log( e.data.hq ); // �o��: 'img/hq_10.jpg'
        }
      });
    });


